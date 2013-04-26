disruptor
=========

<img src="http://anders.com/1offs/disruptor.png" width="400" height="228" alt="disruptor" align="right" />

Warning: This is alpha code. Things are in the design stage so they may change without notice.

**disruptor** intends to be a distributed fault-tolerant real-time computation node.js platform. It 
has minimal configuration requirements and no single point of failure. Nodes are told about one other 
peer when they are started and eventually find all the other live peers in a network. Compute jobs 
written in javascript with json data payloads are sent to any node in the network which distributes
the job amongst the live nodes. Results are then collated and returned to the requestor. There is no 
master peer, monitoring node or other single point of failure and simplicity is stressed throught the 
system. Eventually, disruptor may include a distributed hash table and / or filesystem.

Install
-----
    git clone https://github.com/anders94/disruptor.git

or

    npm install disruptor

Usage
-----
The application takes an IP and port on which to listen and the IP and port of some other peer 
on the network. All the peers will find eachother and stay in communication as peers enter and
leave the network.

    node peer myHost:myPort anotherHost:anotherPort

Example
-------
In the first shell:

    node peer 127.0.0.1:1111 127.0.0.1:22222

In the second shell:

    node peer 127.0.0.1:2222 127.0.0.1:11111

The processes should find eachother. Start a few more and point each to one of the live nodes in 
the network and they should all find eachother.

To see what nodes the first process knows about, visit the peer in a browser:

    http://127.0.0.1:1111

TODO
----
* support a compute request on a single node
** accept some code to execute
** accept some data to work with
** run the job
** return the result to the requestor
* enable a single computational request to one of the nodes
** send the request to all nodes this node knows about
** wait for all the responses
** sew up all the results and feed them back to the requestor

Author
------
**Anders Brownworth**

+ [http://twitter.com/anders94](http://twitter.com/anders94)
+ [http://github.com/anders94](http://github.com/anders94)
+ [http://anders.com/](http://anders.com)

Please get in touch if you would like to contribute.

Copyright and license
---------------------
Copyright 2013 Anders Brownworth

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work except 
in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:

  [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the 
License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either 
express or implied. See the License for the specific language governing permissions and
limitations under the License.
