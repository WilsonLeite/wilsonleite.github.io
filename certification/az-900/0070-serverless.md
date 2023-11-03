# Describe serverless

It is a type of computing resource where the customer doesn't have to manage servers. 

### Azure Functions

Azure Functions run on demand when invoked, typically have a short execution period and each execution is billed by the time it ran and the amount of resources it used. Is is called serverles because it has a short lifespan and each request can pontentially be executed in different servers. 

In contrast, other forms of computing (VM, Containers, etc) are somehow associated to a physical computer.

### SQL Database

Azure also has a SQL Database tier named serverless. It can scale on-demand and is charged according to the resources used. Optionally, it can be completely paused when inactive.

In contrast, typical database instances have a fixed amount of resources associated to them, leading to fixed costs and a well-defined performance peak.

References:

* [Serverless compute tier for Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/serverless-tier-overview?view=azuresql&tabs=general-purpose)
* PluralSight: [Functions](https://app.pluralsight.com/course-player?clipId=fb2250be-88ab-44ce-8884-d867c175bb6a)


