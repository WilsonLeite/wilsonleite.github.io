## Describe the benefits of reliability and predictability in the cloud

Reliability is related to large-scale disaster recovery. That is achieved by replicating resources among geographycally dispersed servers. This can be as close as servers in different parts of the same building to as far as servers allocated in different continents. Some resources - like storage - can be allocated with an intrinsic level or geographycal replication and Azure will take care of it automatically. Other resources - typically network related - allows the Azure customer to design a geographically distributed system where the client traffic will be rerouted automatically in case of an outage.

Predictability 
* Performance: autoscaling, load balancing, high availability
* Cost: The cost is proportional to the resources used and can be monitored in real-time

References:

* Microsoft Learn: [Describe the benefits of reliability and predictability in the cloud](https://learn.microsoft.com/en-us/training/modules/describe-benefits-use-cloud-services/3-reliability-predictability-cloud)
