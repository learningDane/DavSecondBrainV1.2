#uni 
The world Wide Web (WWW) is only a part of the internet.
Before the internet, in a call, the caller and the receiver where physically connected by an operator, doing a so called ___circuit switching___. By utilising circuit switching it is difficult to have multiple ongoing connections and you waste bandwidth since even silence si communicated.
The first network was ARPANET, in the 1960s, which used instead ___packet switching___. The original message gets broken into numbered packets which are then reconstructed in order at the destination address.
This way is more robust and more efficient compared to circuit switching, because it doesn't rely on only one link and a single link can have multiple connections.
In 1981 we began adopting the ___TCP___/___IP___ (transmission control protocol / internet protocol) communication model.
The invention of WWW is attributed to Sir Tim Berners-Lee, who, along with Robert Cailliau, published a proposal in 1990 for a hypertext system.
These are the fundamentals features of the web:
1. an URL to identify a resource
2. the HTTP protocol to define how requests and responses operate
3. a Web Server Software that can respond to HTTP requests
4. HTML to publish documents
5. a Browser to make HTTPS requests from URLS and to display the HTML it receives. 
# Web Apps
Web apps are easier to maintain since a web application is accessible by any machine connected to the internet with a browser so you only need to update the server side application. This also means centralized storage.
The disadvantages are:
1. you need an internet connection
2. security concerns
3. storage and licensing
4. compatibility issues
5. limited access to operating system
# Intranet
This is a network limited to a company or else. Because of intranets being private search engines have limited access to the data within. Agents from outside could still be able to reach this data through a [[Firewall]].
# Static Web Page 
These only consist of HTML, they only visualize information.
# Dynamic Web Sites
A user requests to see a certain application, the server runs it and sends the HTML output to the client, being then displayed by the browser.
# Web 2.0
This refers to an interactive experience where users can contribute and consume web content. This requires JavaScript, a programming language used to code client-side applications, run on the client browser.
# The four layer Network Model
1. application layer: http, ftp, pop, etc
2. transport layer: tcp, udp
3. internet layer: IPv4, IPv6
4. link layer: MAC
Every layer relies on the ones under it.
# IP Addresses
We are finishing the possible 4.2 billion addresses granted by the IPv4 Protocol, so we are slowly moving to IPv6.
Your IP address will be generally assigned to you by your ___Internet Service Provider (ISP)___.
In a local network, computers share a single IP address utilizing NAT.
# Transport Layer
This ensures that the communication is effective and makes so that the connection is between processes, not Hosts. In the TCP protocol an ACK packet is sent back to sender with every received package, confirming the arrival of the original message.
In case of a missing package, the TCP makes sure to send it again, until confirmation of arrival.
# Client-Server Model
There are 2 actors:
1. Server: computer agent normally active 24/7, listening for queries by clients
2. Client: this initiates a request to a server and gets a response
# Peer to Peer Model
Other model where every agent is at the same level, functionally identical, each node is able to communicate with one another. Commonly used to illegally share data and with a low cost of maintenance by the developer.
# Server Types
Often a Server is a network of computer, seen from the exterior as a single one. This can be because of separation of roles (web server, email server, data server, application server) or because of scale and amount of requests, in this case a ___load balancer___ (a special router) distributes the load between different computers. You can use a server farm even only for ___failover redundancy___ and not strictly for scale.
# Data Center
These are the structures where server farms are hosted.
For preventing downtimes most large web sites will exist in mirrored data centers in different parts of the country or even the world.
# NAT
Network Address Translation. It is operated by a Router, it translates the IPaddress used privately inside the home net, in the router's IPaddress followed by the port used by the process.
The WAN side address is the public IP, the LAN side address is the private IP used inside the home net.
The router translates the LAN S A and the port, in the WAN S A and the port, while sending and receiving.
# Autonomous System
Every major entity has it's autonomous system and when needed they communicate with eachother. When trying to reach a certain system you may traverse a variety of others, needed as infrastructure for arriving to your destination.
These communications between systems are operated by ___Internet Exchange Points___ (IXP). There are circa 20 so called Tier 1 IXPs which are enormous and free and are able to reach every autonomous system.
Large websites now not only connect to IXPs but now also are connected to multiple other networks as a way of improving the performance of their sites, since _physical distance is a problem_ (latency). 
Sometimes companies mirror data centers in data centers located near IXPs.
# Domain Name System (DNS)
The user requests to the DNS the IP address of a said website, the DNS provides it and the machine accesses the server of the website.
# Domain Levels
server1.www.website.com
1. server1 = fourth level domain
2. www = third level domain
3. website = second level domain (SLD)
4. com = top level domain (TLD)
with the last being the more specific.
Generic top-level domain (gTLD):
- unrestriced: com, net, org, info
- sponsored: gov, mil, edu, and other
- new TLDs
Country code top-level domain (ccTLD)
- us, ca, uk, au.
- internationalized domain names.
# Name Registration
Domain names are assigned by special organizations called domain name registrars. These companies have been given the permission to do so by the appropriate gTLD and/or cc(TLD)
# Domain Name address resolution process
If the resolution is already in the computer's cache (which is not browser specific but can instead be used by every process) it simply resolves with it, otherwise the request is sent to the primary DNS server, which can give the answer or forward it to higher level DNSs.
# URL
There needs to be a consistent structure to websites so that users can easily access the contents,  the web this is the ___Uniform Resource Locator___, URL.
http://www.website.com/index.php?page=17#article
1. http = protocol, based on the protocol the request is sent on a specific port (80 for http)
2. www.website.com = domain
3. index.php = path
4. page=17 = query string
5. article = fragment
### Query String
### HTTP
The Hypertext Transfer Protocol estabilishes a TCP connection on port 80 (by default). There are ports for multiplexing and demultiplexing. To a request, the server responds with a response code, headers and an optional message, which can include file content.
The most common http requests are GET and POST.
Request specifies:
1. client browser, OPsystem
2. accepted formats
3. accepted language
4. accepted encoding
5. to keep alice TCP connection
6. cache control
Answer specifies:
1. timestamp
2. server type
3. content enconding, lenghth and type
4. Content (HTML, CSS, JS)
##### Response Codes
- 2## codes are for successful responses
- 3## redirection-related responses
- 4## client errors
- 5## server errors
# Web Servers
A web server is fundamentally a computer that responds to http requests. Regardless of the physical aspects of a particular server, one must run a [[Software Stack]]. 