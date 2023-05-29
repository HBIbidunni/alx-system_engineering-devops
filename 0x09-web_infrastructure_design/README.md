# ALX Project: Web infrastructure design
------------

### Task 0:

A lot of websites are powered by simple web infrastructure, a lot of time it is composed of a single server with a LAMP stack.

On a whiteboard, design a one server web infrastructure that hosts the website that is reachable via www.foobar.com. Start your explanation by having a user wanting to access your website.

Requirements:

You must use:
1 server
1 web server (Nginx)
1 application server
1 application files (your code base)
1 database (MySQL)
1 domain name foobar.com configured with a www record that points to your server IP 8.8.8.8
You must be able to explain some specifics about this infrastructure:
What is a server
What is the role of the domain name
What type of DNS record www is in www.foobar.com
What is the role of the web server
What is the role of the application server
What is the role of the database
What is the server using to communicate with the computer of the user requesting the website
You must be able to explain what the issues are with this infrastructure:
SPOF
Downtime when maintenance needed (like deploying new code web server needs to be restarted)
Cannot scale if too much incoming traffic
Please, remember that everything must be written in English to further your technical ability in a variety of settings.


### Task 0 solved:

To design a one-server web infrastructure that hosts the website reachable via www.foobar.com, it is important to  break down the components and their roles, starting with the user's request to access the website.

User Access Request:

The user types "www.foobar.com" in their web browser.
Domain Name and DNS:

A domain name is a human-readable name used to identify a website (e.g., "foobar.com").
DNS (Domain Name System) is a system that translates domain names into IP addresses.
The domain name "foobar.com" needs to be configured with a "www" record that points to the server's IP address, which in this case is 8.8.8.8.
The "www" part in www.foobar.com is a DNS record called a subdomain, commonly used for web services.
Server:

A server is a computer that provides services or resources to other computers (clients) over a network.
In this case, we have one server that will handle the website's infrastructure.
Web Server (Nginx):

A web server is a software that serves web pages to clients.
Nginx is a popular web server software known for its performance and scalability.
The web server receives the user's request for www.foobar.com and processes it.
Application Server:

An application server is responsible for executing the web application's logic and generating dynamic content.
It works in conjunction with the web server to handle the user's request.
The application server executes the codebase (your application files) to generate the appropriate response for the user.
Application Files (Codebase):

These are the files containing the code for the website/application.
The application files are stored on the server and are executed by the application server when needed.
Database (MySQL):

A database is used to store and manage data for the website/application.
MySQL is a popular open-source relational database management system.
The database stores and retrieves data required by the application, such as user information, blog posts, etc.
User-Server Communication:

When the user requests www.foobar.com, the communication occurs over the internet.
The server, with its IP address 8.8.8.8, receives the user's request and processes it through the web server and application server.
The server generates the appropriate response, such as a web page, and sends it back to the user's computer for display.
Issues with this Infrastructure:

Single Point of Failure (SPOF):

This infrastructure has a single server, which means that if the server fails, the entire website/application will become unavailable.
To mitigate this, redundancy can be introduced, such as using multiple servers in a load-balanced configuration.
Downtime during Maintenance:

Whenever maintenance or updates are required, such as deploying new code, the web server needs to be restarted.
During this time, the website/application will be temporarily unavailable.
To minimize downtime, strategies like using multiple servers in a load-balanced setup can be employed.
Limited Scalability:

With only one server, this infrastructure may not handle high levels of incoming traffic effectively.
As the traffic increases, the server may become overloaded, causing slow response times or even crashing.
Scaling options, such as adding more servers or utilizing cloud infrastructure, can be explored to handle increased traffic efficiently.
Overall, while the one-server web infrastructure with a LAMP stack can serve a basic website, it has limitations in terms of redundancy, scalability, and downtime during maintenance





### Task 1:

On a whiteboard, design a three server web infrastructure that hosts the website www.foobar.com.

Requirements:

You must add:
2 servers
1 web server (Nginx)
1 application server
1 load-balancer (HAproxy)
1 set of application files (your code base)
1 database (MySQL)
You must be able to explain some specifics about this infrastructure:
For every additional element, why you are adding it
What distribution algorithm your load balancer is configured with and how it works
Is your load-balancer enabling an Active-Active or Active-Passive setup, explain the difference between both
How a database Primary-Replica (Master-Slave) cluster works
What is the difference between the Primary node and the Replica node in regard to the application
You must be able to explain what the issues are with this infrastructure:
Where are SPOF
Security issues (no firewall, no HTTPS)
No monitoring
Please, remember that everything must be written in English to further your technical ability in a variety of settings.


### Task 1 solved:

To design a three-server web infrastructure that hosts the website www.foobar.com, it is important to  break down the components and their roles, starting with the user's request to access the website.

User Access Request:

The user types "www.foobar.com" in their web browser.
Server 1:

This is the first server in the infrastructure.
It will act as the web server (Nginx) responsible for serving web pages to clients.
The web server receives the user's request and processes it.
Server 2:

This is the second server added to the infrastructure.
It will act as the application server responsible for executing the web application's logic and generating dynamic content.
The application server works in conjunction with the web server to handle the user's request.
Load Balancer (HAproxy):

A load balancer distributes incoming traffic across multiple servers to improve performance, scalability, and reliability.
In this infrastructure, a load balancer (HAproxy) is added to distribute the user requests between the web server and application server.
It uses a distribution algorithm to determine how to route the traffic.
Distribution Algorithm:

The load balancer is configured with a distribution algorithm to determine how it distributes traffic among the servers.
One common algorithm is round-robin, where each server receives an equal share of requests in a sequential manner.
Active-Active vs. Active-Passive Setup:

An Active-Active setup means that all servers are actively serving traffic simultaneously.
An Active-Passive setup means that only one server is active, while the others are on standby as backups.
In this infrastructure, with multiple servers and a load balancer, it is an Active-Active setup as all servers are actively serving traffic.
Application Files (Codebase):

These are the files containing the code for the website/application.
The application files are stored on the application server and executed when needed.
Database (MySQL):

A database is used to store and manage data for the website/application.
In this infrastructure, a MySQL database is added to store data.
A Primary-Replica (Master-Slave) cluster is implemented for database replication and high availability.
Primary-Replica Cluster:

The database cluster consists of a Primary (Master) node and one or more Replica (Slave) nodes.
The Primary node handles write operations (inserts, updates, deletes) and replicates data to the Replica nodes.
The Replica nodes handle read operations, improving scalability and fault tolerance.
Difference Between Primary and Replica Nodes:

The Primary node is responsible for processing write operations and maintaining the authoritative copy of the data.
The Replica nodes replicate data from the Primary node and handle read operations to distribute the load and improve performance.
Issues with this Infrastructure:

Single Point of Failure (SPOF):

This infrastructure may have single points of failure, such as the web server, application server, or database.
To mitigate this, redundancy can be introduced, such as using multiple servers and ensuring high availability configurations for critical components.
Security Issues:

The infrastructure lacks a firewall and HTTPS (secure communication protocol).
Without a firewall, the servers are more vulnerable to attacks and unauthorized access.
Without HTTPS, the communication between the website and users is not encrypted, which can expose sensitive data.
Implementing a firewall and enabling HTTPS would enhance security.
Lack of Monitoring:

The infrastructure does not include monitoring tools or practices.
Monitoring is crucial for observing server and application performance.

