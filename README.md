# duct
(d)istributed (u)nscientific (c)as (t)est

Just to be a simple command line utility to do quick smoke tests of multi-CAS nodes deployments. In particular, testing correctness of data sharing between nodes by implementations of distributed ticket registries. The initial version of test should just automate very simple scenario:

* Authenticate and issue a service ticket on one CAS node
* Validate this service ticket on the other node

If this test succeeds, then we effectively have proven that the distributed ticket registry has been set up and deployed correctly and that there are no connectivity issues between CAS nodes.

> No code yet. Thinking to implement this in Groovy. We'll see...
