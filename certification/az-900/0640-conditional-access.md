## Describe Conditional Access in Azure AD

<< What is the relationship between Conditional Access and Entra ID? >>

During sign-in, Conditional Access collects extra signals from the users like their location, the devices their are using, or the application that the user is trying to access. It then use that information to allow or deny access or to require multifactor authentication.

![Conditional Access](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/conditional-access-9bd268b8.png)

Use cases:
* Require multifactor authentication (MFA) to access an application depending on the requester’s role, location, or network. For example, requiring MFA for administrators but not regular users or for people connecting from outside your corporate network.

* Require access to services only through approved client applications. For example, limiting which email applications are able to connect to the email service.

* Require users to access the application only from managed devices. A managed device is a device that meets standards for security and compliance.

* Block access from untrusted sources, such as access from unknown or unexpected locations.

<< Is there a comprehensive list of types of signals? Can we create our own? >>

References:

* Microsoft Learn: [Describe Azure conditional access](https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/5-conditional-access)
