# Describe Azure Monitor, including Log Analytics, Azure Monitor alerts, and Application Insights

Azure collects signals from several sources: audit logs, activity logs, service health, metrics, logs, etc. These signals come from each layer, from Entra ID to resource telemetry.

Azure Monitor aggregates all these signals and provide a few services:
* _Visualize the data_: both in real-time and historical data. It can be aggregated or detailed.
* _Alerts_: Send messages or trigger actions based on the collected signals.

### Azure Log Analytics

It is the tool in the Azure Portal allowing writing and running log queries on the data gathered by Azure Monitor. It supports sorting and filtering, as well as visualize the results in a chart.

### Azure Monitor Alerts

It is a tool that supports the creation of alerts and continuously monitors the signals that trigger them.

Alerts input:
* Metrics going beyond a threshold
* Log events

Output: Action groups
* Messages (SMS, e-mail)
* Triggered actions (autoscaling, etc.)

### Application Insights

It monitors web applications by either installing an SDK in the application or using an Application Insights agent. It collects:

* Request rates, response times, and failure rates
* Dependency rates, response times, and failure rates, to show whether external services are slowing down performance
* Page views and load performance reported by users' browsers
* AJAX calls from web pages, including rates, response times, and failure rates
* User and session counts
* Performance counters from Windows or Linux server machines, such as CPU, memory, and network usage

The Application Insights service in Azure may be configured to periodically sending synthetic requests to the application, allowing getting telemetry even during periods of low activity.

References:

* Microsoft Learn: [Describe Azure Monitor](https://learn.microsoft.com/en-us/training/modules/describe-monitoring-tools-azure/4-describe-azure-monitor)
