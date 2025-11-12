<!-- loiod013ab9d41ba4016871f0e9c17c77a3e -->

# Transformation to OTLP Logs

Learn how the log agent processes the original container logs and transforms them into structured OpenTelemetry \(OTLP\) log records.



<a name="loiod013ab9d41ba4016871f0e9c17c77a3e__section_sv5_2tf_bgc"/>

## Original Log Message

The following example shows a container `myContainer` in Pod `myPod`, running in namespace `myNamespace`, logging to `stdout` with the following JSON message:

```
{
  "level": "warn",
  "message": "This is the original message",
  "tenant": "myTenant",
  "traceID": "123"
}

```



<a name="loiod013ab9d41ba4016871f0e9c17c77a3e__section_log_tailing"/>

## Log Tailing

The log agent reads the log message from a log file managed by the container runtime. The file name contains namespace, Pod, and container information that becomes available later as log attributes. The raw log record looks like the following example:

```
{
  "time": "2022-05-23T15:04:52.193317532Z",
  "stream": "stdout",
  "_p": "F",
  "log": "{\"level\": \"warn\",\"message\": \"This is the original message\",\"tenant\": \"myTenant\",\"trace_id\": \"123\"}"
}

```

After the tailing, the created OTLP record looks like the following example:

```
{
  "time": "2022-05-23T15:04:52.100000000Z",
  "observedTime": "2022-05-23T15:04:52.200000000",
  "attributes": {
   "log.file.path": "/var/log/pods/myNamespace_myPod-<containerID>/myContainer/<containerRestarts>.log",
   "log.iostream": "stdout"
  },
  "resourceAttributes": {
    "k8s.container.name": "myContainer",
    "k8s.container.restart_count": "<containerRestarts>",
    "k8s.pod.name": "myPod",
    "k8s.namespace.name": "myNamespace"
  },
  "body": "{\"level\": \"warn\",\"message\": \"This is the original message\",\"tenant\": \"myTenant\",\"trace_id\": \"123\"}"
}

```

The log agent enriches all information identifying the log source \(such as container, Pod, and namespace name\) as resource attributes, following [Kubernetes conventions](https://opentelemetry.io/docs/specs/semconv/resource/k8s/). It enriches further metadata, like the original file name and channel, as log attributes, following [log attribute conventions](https://opentelemetry.io/docs/specs/semconv/general/logs/). The agent uses the `time` value from the container runtime's log entry as the `time` attribute in the new OTel record, as it closely matches the actual log event time. Additionally, the agent sets `observedTime` with the time it actually reads the log record, as the OTel log specification recommends. The agent moves the log payload to the OTLP `body` field.



<a name="loiod013ab9d41ba4016871f0e9c17c77a3e__section_json_parsing"/>

## JSON Parsing

If the `body` value is a JSON document, the agent parses the value and enriches all JSON root attributes as additional log attributes. The agent moves the original body into the `log.original` attribute \(managed with the `LogPipeline` attribute `input.application.keepOriginalBody: true`\).

After JSON parsing, the OTLP record looks like the following example:

```
{
  "time": "2022-05-23T15:04:52.100000000Z",
  "observedTime": "2022-05-23T15:04:52.200000000",
  "attributes": {
   "log.file.path": "/var/log/pods/myNamespace_myPod-<containerID>/myContainer/<containerRestarts>.log",
   "log.iostream": "stdout",
   "log.original": "{\"level\": \"warn\",\"message\": \"This is the original message\",\"tenant\": \"myTenant\",\"trace_id\": \"123\"}",
   "level": "warn",
   "tenant": "myTenant",
   "trace_id": "123",
   "message": "This is the original message"
  },
  "resourceAttributes": {
    "k8s.container.name": "myContainer",
    "k8s.container.restart_count": "<containerRestarts>",
    "k8s.pod.name": "myPod",
    "k8s.namespace.name": "myNamespace"
  },
  "body": ""
}

```



<a name="loiod013ab9d41ba4016871f0e9c17c77a3e__section_severity_parsing"/>

## Severity Parsing

Typically, a log message includes a log level in the `level` field. Based on this, the agent parses the `level` log attribute with a severity parser. If parsing succeeds, the agent transforms the log attribute into the OTel attributes `severityText` and `severityNumber`.



<a name="loiod013ab9d41ba4016871f0e9c17c77a3e__section_trace_parsing"/>

## Trace Parsing

OTLP natively attaches trace context to log records. If possible, the log agent parses the following log attributes according to the [W3C-Tracecontext specification](https://www.w3.org/TR/trace-context/#traceparent-header):

-   `trace_id`

-   `span_id`

-   `trace_flags`

-   `traceparent`




<a name="loiod013ab9d41ba4016871f0e9c17c77a3e__section_log_body_determination"/>

## Log Body Determination

Because the original log message typically resides in the `body` attribute, the agent moves a log attribute called `message` \(or `msg`\) into the body.

At this point, before further enrichment, the resulting overall log record looks like the following example:

```
{
  "time": "2022-05-23T15:04:52.100000000Z",
  "observedTime": "2022-05-23T15:04:52.200000000",
  "attributes": {
   "log.file.path": "/var/log/pods/myNamespace_myPod-<containerID>/myContainer/<containerRestarts>.log",
   "log.iostream": "stdout",
   "log.original": "{\"level\": \"warn\",\"message\": \"This is the original message\",\"tenant\": \"myTenant\",\"trace_id\": \"123\"}",
   "tenant": "myTenant",
  },
  "resourceAttributes": {
    "k8s.container.name": "myContainer",
    "k8s.container.restart_count": "<containerRestarts>",
    "k8s.pod.name": "myPod",
    "k8s.namespace.name": "myNamespace"
  },
  "body": "This is the original message",
  "severityNumber": 13,
  "severityText": "warn",
  "trace_id": 123
}

```

This structured record is now ready to be shipped to your observability backend. For details on further enrichment, see [Automatic Data Enrichment](automatic-data-enrichment-6a13459.md).

