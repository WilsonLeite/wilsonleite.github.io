## Describe the concept of Zero Trust

Zero Trust is a security model that does not assume that a request is secure just because it originated from a secure perimeter (network, etc.) or a trusted computer. Instead of assuming that a device is safe because it’s within the corporate network, it requires everyone to authenticate. Then grants access based on authentication rather than location.

It's implementation is based on these guiding principles:

* Verify explicitly - Always authenticate and authorize based on all available data points.
* Use least privilege access - Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.
* Assume breach - Minimize blast radius and segment access. Verify end-to-end encryption. Use analytics to get visibility, drive threat detection, and improve defenses.

References:

* Microsoft Learn: [Describe zero trust model](https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/7-describe-zero-trust-model)
