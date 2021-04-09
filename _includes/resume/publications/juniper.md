#### [A Systematic Analysis of the Juniper Dual EC Incident](https://checkoway.net/papers/juniper2016/juniper2016.pdf) - *ACM CCS 2016*
{: #juniper}

**October 2016** - *research, security, cryptography, reverse engineering*

In December 2015, Juniper Networks announced multiple security
vulnerabilities from unauthorized code in ScreenOS. I worked with Stephen
Checkoway, Matt Green, Nadia Heninger, and others to reverse engineer the
ScreenOS firmware and demonstrate the vulnerabilities. We determined that the
passive VPN decryption issue was a result of a series of intentional design
choices based around the Dual EC random number generator.

