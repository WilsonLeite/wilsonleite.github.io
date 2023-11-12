## Identify appropriate use cases for each cloud service (IaaS, PaaS, and SaaS)

IaaS:
* Lift-and-shift migration: Move from a physical infrastructure to corresponding virtualized resources
* Testing and development: Resources that are used intermittently can be shut down and restarted as needed, saving costs and allowing fast configuration switching. In constrast, some PaaS and SaaS resources are not that flexible. For example, instances of Azure SQL Database cannot be stopped once created. (UPDATE: The [Serverless](https://learn.microsoft.com/en-ca/azure/azure-sql/database/serverless-tier-overview?view=azuresql&tabs=general-purpose#overview) tier supports being automatically stopped after an auto-pause delay)

PaaS:
* Development framework: Databases, network drives, container orchestrators, etc.
* [Analytics](https://azure.microsoft.com/en-ca/products/#analytics) or [business intelligence](https://azure.microsoft.com/en-ca/solutions/business-intelligence)

SaaS:
* Applications ready to use by the end users:
    * Email and messaging
    * Business productivity applications
    * Finance and expense tracking

### References

Microsoft Learn

* [Describe Infrastructure as a Service](https://learn.microsoft.com/en-us/training/modules/describe-cloud-service-types/2-describe-infrastructure-service)
* [Describe Platform as a Service](https://learn.microsoft.com/en-us/training/modules/describe-cloud-service-types/3-describe-platform-service)
* [Describe Software as a Service](https://learn.microsoft.com/en-us/training/modules/describe-cloud-service-types/4-describe-software-service)