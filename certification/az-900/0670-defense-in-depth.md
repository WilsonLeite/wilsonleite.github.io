## Describe the purpose of the defense-in-depth model



![Defense in depth](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/defense-depth-486afc12.png)

Brief overview of the role of each layer:

* The physical security layer is the first line of defense to protect computing hardware in the datacenter.
    * Datacenter, hardware
* The identity and access layer controls access to infrastructure and change control.
    * Authentication, authorization, MFA, audit
* The perimeter layer (DMZ) uses distributed denial of service (DDoS) protection to filter large-scale attacks before they can cause a denial of service for users.
    * Firewall, DDoS protection
* The network layer limits communication between resources through segmentation and access controls.
    * Subnet, Firewall, explicit routes, restrict inbound, outbound and inter-resource traffic.
* The compute layer secures access to virtual machines.
    * Endpoint protection and OS patching
* The application layer helps ensure that applications are secure and free of security vulnerabilities.
    * Secure by design (Authentication, authorization), secure storage of secrets
* The data layer controls access to business and customer data.
    * Controls and processes to ensure confidentiality, integrity, and availability

### References:

Microsoft Learn 

* [Describe defense-in-depth](https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/8-describe-defense-depth)
* [Datacenter security overview](https://learn.microsoft.com/en-us/compliance/assurance/assurance-datacenter-security)
