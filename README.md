# duct
(d)istributed (u)nscientific (c)as (t)est

> This project was developed as part of Unicon's [Open Source Support program](https://unicon.net/opensource).
Professional Support / Integration Assistance for this module is available. For more information [visit](https://unicon.net/opensource/cas).

`duct` is a simple command line utility to do quick smoke tests of multi-CAS nodes deployments. In particular, testing correctness of data sharing between `2` nodes by implementations of distributed ticket registries. The initial version of this program just automates a very simple scenario:

* Authenticate and issue a service ticket on one CAS node
* Validate this service ticket on the other node

If this test succeeds, then we effectively have proven that the distributed ticket registry has been set up and deployed correctly and that there are no connectivity issues between CAS nodes.

This utility requires CAS server nodes to enable `REST` module.

## Prerequisites

* Latest JDK and Groovy (always a good idea to have the latest installed)
* 2 CAS nodes with a distributed TicketRegistry configured (EhCache, Hazelcast, etc.) and REST endpoints enabled

  > Note: for CAS 3.5.x, the easiest way to enable REST is to install [CAS REST addon](https://github.com/unicon-cas-addons/cas35-addon-rest)

## Installation

* Download `duct.conf` and place it in `/etc/duct`
* Configure `duct.conf` according to your environment

  > duct.conf is self-explanatory. All values are required. The base file that is included looks like this:
  
  ```Groovy
    //All values are required. All Strings except cas.rest.connection.timeout
    cas {
      username='casuser'
      password='casuser'
      service='https://www.google.com'
      rest.connection.timeout=3000 //must be positive integer (milliseconds)
      url {
        node1='https://dk.example.org:8143/cas'
        node2='https://dk.example.org:8243/cas'
      }
    }
  ```
  * Download `duct` file (for ease of invoking it, it could be placed somewhere in the user's `$PATH` e.g. `/usr/local/bin`
  * Make `duct` file executable i.e. `chmod 755 duct`
  
## Running

* Make sure 2 CAS nodes that need verification are running
* Make sure that `/etc/duct/duct.conf` is properly configured
* From the command line execute `./duct` or simply `duct` if it has been placed on the user's `$PATH`
