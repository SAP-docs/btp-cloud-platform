<!-- loioef499954a5fa44fdbca726f6bf159ef0 -->

# New Runtime API

The `nodejs26` and `python314` runtimes introduce a new handler API that removes the `event` and `context` wrapper objects. Handlers receive the raw HTTP framework objects directly, and function metadata is provided by an explicit `sdk` module.



<a name="loioef499954a5fa44fdbca726f6bf159ef0__section_handler_signature"/>

## Handler Signature

In the legacy runtimes \(`nodejs22`, `nodejs24`, `python312`\), every handler received `event` and `context` arguments injected by the runtime. In the new runtimes, handlers work directly with the underlying HTTP framework.



### Node.js

The handler now receives raw Express `req` and `res` objects instead of the custom `event` and `context`.


<table>
<tr>
<th valign="top">

Before \(nodejs22/nodejs24\)

</th>
<th valign="top">

After \(nodejs26\)

</th>
</tr>
<tr>
<td valign="top">

`main(event, context)`

</td>
<td valign="top">

`main(req, res)`

</td>
</tr>
</table>

```
// Before
module.exports = {
    main: function (event, context) {
        return "Hello, " + event.data.name;
    }
}
```

```
// After
module.exports = {
    main: function (req, res) {
        res.send("Hello, " + req.body.name);
    }
}
```



### Python

The handler now takes no arguments. The incoming request is available through Flask's `flask.request` context-local.


<table>
<tr>
<th valign="top">

Before \(python312\)

</th>
<th valign="top">

After \(python314\)

</th>
</tr>
<tr>
<td valign="top">

`main(event, context)`

</td>
<td valign="top">

`main()`

</td>
</tr>
</table>

```
# Before
def main(event, context):
    return "Hello, " + event.data["name"]
```

```
# After
import flask

def main():
    data = flask.request.get_json()
    return "Hello, " + data["name"]
```



<a name="loioef499954a5fa44fdbca726f6bf159ef0__section_sdk_module"/>

## SDK Module

In the legacy runtimes, function metadata was available through the `context` object and tracing through `event.tracer`. In the new runtimes, an explicit `sdk` module replaces both. For the full SDK reference, see [Function's Specification](https://kyma-project.io/external-content/serverless/docs/user/technical-reference/07-70-function-specification.html#sdk-module).



### Node.js

```
// Before — context fields and event.tracer
module.exports = {
    main: async function (event, context) {
        const tracer = event.tracer;
        console.log(context['function-name']);
        console.log(context['namespace']);
        console.log(context['runtime']);
        console.log(context['timeout']);
        console.log(context['body-size-limit']);
    }
}
```

```
// After — sdk functions
const { getTracer, getFunctionName, getNamespace, getRuntime, getTimeout, getBodySizeLimit } = require('sdk');

module.exports = {
    main: async function (req, res) {
        const tracer = getTracer();
        console.log(getFunctionName());
        console.log(getNamespace());
        console.log(getRuntime());
        console.log(getTimeout());
        console.log(getBodySizeLimit());
        res.send('ok');
    }
}
```



### Python

```
# Before — context fields and event.tracer
def main(event, context):
    tracer = event.tracer
    print(context['function-name'])
    print(context['namespace'])
    print(context['runtime'])
    print(context['timeout'])
    print(context['body-size-limit'])
    return "ok"
```

```
# After — sdk functions
import sdk

def main():
    tracer = sdk.get_tracer()
    print(sdk.get_function_name())
    print(sdk.get_namespace())
    print(sdk.get_runtime())
    print(sdk.get_timeout())
    print(sdk.get_body_size_limit())
    return "ok"
```



<a name="loioef499954a5fa44fdbca726f6bf159ef0__section_cloudevent_handling"/>

## CloudEvent Handling

In the legacy runtimes, CloudEvent attributes were spread as individual string keys on the `event` object \(for example, `event['ce-type']`\). In the new runtimes, `getCloudEvent()` / `sdk.get_cloud_event()` returns a standard `CloudEvent` object with typed properties.



### Node.js

```
// Before — CloudEvent fields were individual keys on the event object
module.exports = {
    main: async function (event, context) {
        if (event['ce-type']) {
            console.log(event['ce-type']);
            console.log(event['ce-source']);
            // eventtypeversion was dropped in CloudEvents version 0.2
            // console.log(event['ca-eventtypeversion']);
            console.log(event['ce-specversion']);
            console.log(event['ce-id']);
            console.log(event['ce-time']);
            console.log(event['ce-datacontenttype']);
            console.log(event['data']);
            return event['ce-type'];
        }
        return "not a cloud event";
    }
}
```

```
// After — getCloudEvent() returns a standard CloudEvent object
const { getCloudEvent } = require('sdk');

module.exports = {
    main: function (req, res) {
        const ce = getCloudEvent(req);
        if (ce) {
            console.log(ce.type);
            console.log(ce.source);
            console.log(ce.specversion);
            console.log(ce.id);
            console.log(ce.time);
            console.log(ce.datacontenttype);
            console.log(ce.data);
            res.send(ce.type);
            return;
        }
        res.send("not a cloud event");
    }
}
```



### Python

```
# Before — CloudEvent fields were individual keys on the event object
def main(event, context):
    if event['ce-type']:
        print(event['ce-type'])
        print(event['ce-source'])
        # eventtypeversion was dropped in CloudEvents version 0.2
        # print(event['ce-eventtypeversion'])
        print(event['ce-specversion'])
        print(event['ce-id'])
        print(event['ce-time'])
        print(event['ce-datacontenttype'])
        print(event['data'])
        return event['ce-type']
    return "not a cloud event"
```

```
# After — get_cloud_event() returns a standard CloudEvent object
import sdk

def main():
    ce = sdk.get_cloud_event()
    if ce:
        print(ce.get_type())
        print(ce.get_source())
        print(ce.get_specversion())
        print(ce.get_id())
        print(ce.get_time())
        print(ce.get_datacontenttype())
        print(ce.get_data())
        return ce.get_type()
    return "not a cloud event"
```



<a name="loioef499954a5fa44fdbca726f6bf159ef0__section_emitting_cloudevents"/>

## Emitting CloudEvents

In the legacy runtimes, CloudEvents were emitted through `event.emitCloudEvent()`. In the new runtimes, `emitCloudEvent` is imported directly from the `sdk` module.



### Node.js

```
// Before
module.exports = {
    main: async function (event, context) {
        await event.emitCloudEvent(
            'com.example.order.created',
            '/orders',
            { orderId: '123' }
        );
        return "event emitted";
    }
}
```

```
// After
const { emitCloudEvent } = require('sdk');

module.exports = {
    main: async function (req, res) {
        await emitCloudEvent(
            'com.example.order.created',
            '/orders',
            { orderId: '123' }
        );
        res.send("event emitted");
    }
}
```



### Python

```
# Before
def main(event, context):
    event.emitCloudEvent(
        'com.example.order.created',
        '/orders',
        {'orderId': '123'}
    )
    return "event emitted"
```

```
# After
import sdk

def main():
    sdk.emit_cloud_event(
        'com.example.order.created',
        '/orders',
        {'orderId': '123'}
    )
    return "event emitted"
```



<a name="loioef499954a5fa44fdbca726f6bf159ef0__section_http_responses"/>

## HTTP Responses



### Node.js

In the legacy runtimes, a handler could return a value directly and the runtime would send it as the response body. In `nodejs26`, return values are ignored — the `res` object must be used explicitly.

```
// Before
module.exports = {
    main: function (event, context) {
        return { statusCode: 400, body: "Bad request" };
    }
}
```

```
// After
module.exports = {
    main: function (req, res) {
        res.status(400).send("Bad request");
    }
}
```



### Python

In `python314`, return values work the same way as in `python312` — Flask response tuples are supported.

```
# Before
def main(event, context):
    return "Bad request", 400
```

```
# After — no change needed
def main():
    return "Bad request", 400
```



<a name="loioef499954a5fa44fdbca726f6bf159ef0__section_environment_variables"/>

## Environment Variables

The following environment variables were renamed in the new runtimes. The `FUNC_MEMFILE_MAX` variable also changed its unit from bytes to megabytes.


<table>
<tr>
<th valign="top">

Old name

</th>
<th valign="top">

New name

</th>
<th valign="top">

Runtimes

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

`FUNC_HANDLER`

</td>
<td valign="top">

`HANDLER_FUNC_NAME`

</td>
<td valign="top">

`nodejs26`, `python314`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`MOD_NAME`

</td>
<td valign="top">

`HANDLER_MOD_NAME`

</td>
<td valign="top">

`nodejs26`, `python314`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`REQ_MB_LIMIT`

</td>
<td valign="top">

`FUNC_BODY_MB_LIMIT`

</td>
<td valign="top">

`nodejs26`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`FUNC_MEMFILE_MAX`

</td>
<td valign="top">

`FUNC_BODY_MB_LIMIT`

</td>
<td valign="top">

`python314`

</td>
<td valign="top">

Unit changed from bytes to megabytes

</td>
</tr>
<tr>
<td valign="top">

`KYMA_INTERNAL_LOGGER_ENABLED`

</td>
<td valign="top">

`SERVER_INTERNAL_LOGGER`

</td>
<td valign="top">

`nodejs26`, `python314`

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Related Information**  


[Function's Specification — full SDK reference for nodejs26 and python314](https://kyma-project.io/external-content/serverless/docs/user/technical-reference/07-70-function-specification.html)

[Environment Variables — complete list of runtime environment variables](https://kyma-project.io/external-content/serverless/docs/user/technical-reference/05-20-env-variables.html)

