<!-- loiodbda6badd40a4ab8aacb16f282ac932b -->

# Function Fails to Start With Customized OpenTelemetry Dependencies



## Symptom

After customizing OpenTelemetry dependencies, the Serverless Function is not starting.



## Cause

You can configure your own dependencies as part of the Function's dependencies. While this allows customization, it also introduces the risk of dependency conflicts, especially with OpenTelemetry packages, which have strict version requirements for their dependencies. For example, `opentelemetry-instrumentation` requires specific versions of `opentelemetry-api` and `opentelemetry-sdk`. A version mismatch can lead to runtime errors. Downgrading or upgrading one package without aligning the others can lead to runtime errors or import issues.



## Solution

Avoid downgrading OpenTelemetry packages in your Function's configuration. Use the dependencies provided by the Serverless module for [Python](https://raw.githubusercontent.com/kyma-project/serverless/refs/heads/main/components/runtimes/python312/requirements.txt) and [Node.js](https://raw.githubusercontent.com/kyma-project/serverless/refs/heads/main/components/runtimes/nodejs24/package.json). These dependencies are regularly maintained and upgraded. They are also tested to ensure compatibility.

If you must customize OpenTelemetry dependencies, ensure that all related packages \(e.g., `opentelemetry-api`, `opentelemetry-sdk`, `opentelemetry-instrumentation`\) are aligned to compatible versions. Refer to the [PyPi](https://pypi.org/) and [npm](https://www.npmjs.com/) pages to verify compatibility of the desired version.

