---
title: Interoperability of OpenTelemetry API and Datadog instrumented traces
kind: guide
further_reading:
- link: "/tracing/trace_collection/otel_instrumentation/"
  tag: "Documentation"
  text: "Custom Instrumentation with OpenTelemetry API"
- link: "/tracing/trace_collection/trace_context_propagation/"
  tag: "Documentation"
  text: "Trace Context Propagation in Datadog"

---

## Custom instrumentation with the OpenTelemetry API

Datadog tracing libraries provide an implementation of the [OpenTelemetry API][1] for instrumenting your code. This means you can maintain vendor-neutral instrumentation of all your services, while still taking advantage of Datadog's native implementation, features, and products. 

By [instrumenting your code with OpenTelemetry API][2]:

- Your code remains free of vendor-specific API calls.
- Your code does not depend on Datadog tracing libraries at compile time (only runtime).
- Your code does not use the deprecated OpenTracing API.

Replace the OpenTelemetry SDK with the Datadog tracing library in the instrumented application, and the traces produced by your running code can be processed, analyzed, and monitored alongside Datadog traces and in Datadog proprietary products such as [Continuous Profiler][3], [Data Streams Monitoring][4], [Application Security Management][5], and [Live Processes][6].

## W3C trace context propagation

To facilitate seamless handling of OpenTelemetry trace data within Datadog, and correlating it with trace data generated by Datadog instrumentation, the most recent versions of Datadog tracing libraries support both [Datadog (`datadog`) and W3C (`tracecontext`) propagation styles][8] by default. [Update your runtime tracing library dependencies][7] to the latest version.

This context propagation style allows Datadog tracers to operate in the same application environment with OpenTelemetry SDKs and other W3C compliant tracers.


## 128-bit trace IDs

W3C traces implicitly contain 128-bit trace IDs, rather than the 64-bit trace IDs that Datadog traces have historically used. The latest Datadog tracing libraries default configuration uses the setting `DD_TRACE_128_BIT_TRACEID_GENERATION_ENABLED=True` so that they also produce trace data with 128-bit trace IDs. 

Following the [W3C Trace Context recommendations][9], Datadog 128-bit trace IDs have randomness in the lower-order 64 bits. This restriction provides backward compatibility for systems that intermix libraries that generate 64-bit trace IDs with newer ones that support 128-bit IDs. In such systems, spans with the full 128-bit trace ID and spans with the truncated lower-order 64-bit trace ID can arrive at the backend and be treated as matching and part of the same trace.

{{< img src="opentelemetry/guide/otel_api_tracing_interop/128-62-bit-trace-ids.png" alt="128-bit Trace IDs can be passed with trace context to code whose tracing library generates 64-bit trace IDs, and Datadog successfully correlate them in the backend." style="width:100%;" >}}

## Further reading

{{< partial name="whats-next/whats-next.html" >}}


[1]: https://opentelemetry.io/docs/specs/otel/trace/api/
[2]: /trace_collection/otel_instrumentation/
[3]: /profiler/
[4]: /data_streams/
[5]: /security/application_security/
[6]: /infrastructure/process
[7]: /tracing/trace_collection/dd_libraries/
[8]: /tracing/trace_collection/trace_context_propagation/
[9]: https://www.w3.org/TR/trace-context/#handling-trace-id-for-compliant-platforms-with-shorter-internal-identifiers
