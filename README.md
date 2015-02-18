# duct
(d)istributed (u)nscientific (c)as (t)est

`duct` is a simple command line utility to do quick smoke tests of multi-CAS nodes deployments. In particular, testing correctness of data sharing between `2` nodes by implementations of distributed ticket registries. The initial version of this program just automates a very simple scenario:

* Authenticate and issue a service ticket on one CAS node
* Validate this service ticket on the other node

If this test succeeds, then we effectively have proven that the distributed ticket registry has been set up and deployed correctly and that there are no connectivity issues between CAS nodes.

This utility requires CAS server nodes to enable `REST` module.

## Prerequisites

* Latest JDK and Groovy (always a good idea to have the latest installed)
* 2 CAS nodes with a distributed TicketRegistry configures (EhCache, Hazelcast, etc.) and REST endpoints enabled

  > Note: for CAS 3.5.x, the easiest way to enable REST is to install [CAS REST addon](https://github.com/unicon-cas-addons/cas35-addon-rest)
