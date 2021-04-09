#### [On the Practical Exploitability of Dual EC in TLS Implementations](http://dualec.org/DualECTLS.pdf) - *Usenix Security 2014*
{: #dualec}

**August 2014** - *research, security, TLS*

I worked with Steve Checkoway, Matt Green, DJB, Hovav Shacham, and others to
demonstrate the exploitability of a potential backdoor in NIST's Dual EC random
number generator. Provided that a server uses Dual EC to supply its TLS
connections with randomness, my proof of concept program, given a single passive
network capture of a HTTPS handshake, is able to retrieve the server's
long-lived ECDSA private key.

