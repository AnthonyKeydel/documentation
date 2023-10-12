---
title: Language and Tracer Versions for Profiler Features
kind: documentation
disable_sidebar: true
further_reading:
- link: "/profiler/enabling"
  tag: "Documentation"
  text: "Enabling Profiler"
---

The following table shows a summary of the features available for each language runtime. 
- **Minimum versions** are the minimum required to get access to a particular feature-If you have an earlier version, that feature is not supported. 
- **Recommended versions** are the runtime and tracer versions that give you access to **all** the supported features. Generally speaking, it's best if you update to the latest version of all tracers.

|                                   |   Java  | Python  |      Go      |  Ruby |   Node.js  |  .NET   |   PHP  | Rust/C/C++ |
|-----------------------------------|:-------:|:-------:|:------------:|:------:|:---------:|:-------:|:------:|:----------:|
| Operating systems                 | | | | Linux only | | | CentOS&nbsp;7+ | Linux&nbsp;v4.17+ |
| Minimum runtime version | JDK 8+ [Details][1] | Python&nbsp;2.7+ | Go 1.12+ | Ruby 2.3+ | Node 14+ | .NET&nbsp;Core&nbsp;2.1+, .NET&nbsp;5+, .NET&nbsp;Framework&nbsp;4.6.1+ [Details][2] | PHP 7.1+ [Details][3] |  |
| Recommended runtime version | JDK 11+ | Python 3.6+ | Go 1.12+ | Ruby 2.3+ | Node 14+ | .NET 6+ | PHP 7.1+ | |
| Minimum tracer version   | | 0.35.0 | 1.23.0 | 0.48.0 | 0.23.0 | 2.7.0| | |
| Recommended tracer version |    | 0.50.0  | 1.51.0 | 1.15.0 | 2.12.0 | 2.31.0  | 0.92.0 | |
| **Profile types:** |
| {{< ci-details title="CPU" >}}The time each function spent running on the CPU.{{< /ci-details >}}   | {{< X >}} | {{< X >}} | {{< X >}} | {{< X >}} | private&nbsp;beta<br>tracer&nbsp;2.12.0 | tracer&nbsp;2.15.0 | {{< X >}} | beta<br>tracer&nbsp;0.1.0 |
| {{< ci-details title="Allocation" >}}Number and sizes of memory allocations made by each function, including allocations which were subsequently freed.{{< /ci-details >}}   | JDK 11+ | Python 3.6+<br>tracer&nbsp;0.50.0 | tracer&nbsp;1.47.0 |      |       | beta, .NET 6+<br>tracer&nbsp;2.18.0 | tracer&nbsp;0.88.0 | beta<br>tracer&nbsp;0.9.3 |
| {{< ci-details title="Heap" >}}The amount of heap memory allocated that remains in use.{{< /ci-details >}}   | JDK 11+ | Python 3.6+<br> tracer&nbsp;0.50.0 | {{< X >}} |      | {{< X >}} | beta, .NET 6+<br>tracer&nbsp;2.22.0 |       | beta<br>tracer&nbsp;0.15.0 |
| {{< ci-details title="Locks" >}}The time each function spent waiting for and holding locks, and the number of times each function acquired a lock.{{< /ci-details >}}   | {{< X >}} | tracer&nbsp;0.45.0 | tracer&nbsp;1.47.0 |      |       | .NET 6+<br>tracer&nbsp;2.31.0 |       |      |
| {{< ci-details title="Wall time" >}}The elapsed time spent in each function. Elapsed time includes time when code is running on CPU, waiting for I/O, and anything else that happens while the function is running.{{< /ci-details >}}   | {{< X >}} | {{< X >}} |       | {{< X >}} | {{< X >}} | {{< X >}} | {{< X >}} |       |
| {{< ci-details title="Disk I/O" >}}Description tktk.{{< /ci-details >}}   | {{< X >}} |       |       |       |       |       |       |       |
| {{< ci-details title="Socket I/O" >}}Description tktk.{{< /ci-details >}}   | {{< X >}} |       |       |       |       |       |       |       |
| {{< ci-details title="Exceptions" >}}The number of exceptions raised, including those caught.{{< /ci-details >}}   | {{< X >}} | Python 3.7+ |       |       |       | .NET 5+<br>tracer&nbsp;2.31.0 |  beta<br>tracer&nbsp;0.92.0  |       |
| **Other features:** |
| {{< ci-details title="Code Hotspots" >}}Description tktk.{{< /ci-details >}}   | {{< X >}} | {{< X >}} | {{< X >}} | {{< X >}} | private&nbsp;beta | {{< X >}} | tracer&nbsp;0.71.0 |      |
| {{< ci-details title="Endpoint Profiling" >}}Description tktk.{{< /ci-details >}}   | {{< X >}} | {{< X >}} | {{< X >}} | {{< X >}} | private&nbsp;beta | tracer&nbsp;2.15.0 | tracer&nbsp;0.79.0 |      |
| {{< ci-details title="Timeline View" >}}Description tktk.{{< /ci-details >}}   | beta |       | beta<br>tracer&nbsp;1.51.0 | private&nbsp;beta<br>tracer&nbsp;1.15.0 |       | beta<br>tracer&nbsp;2.30.0 | beta<br>tracer&nbsp;0.89.0 |      |

## Further reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: /profiler/enabling/java/
[2]: /profiler/enabling/dotnet/
[3]: /profiler/enabling/php/