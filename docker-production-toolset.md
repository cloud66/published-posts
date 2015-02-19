## Docker in production from A to Z

If you have tried using Linux containers (like Docker) in production, you are aware of the difficulties surrounding image building, orchestration of containers, logging and monitoring them. 

Cloud 66 simplifies Ops for developers by building, configuring and managing your servers on any cloud. Our Docker support provides a complete toolset for rolling out containers to production on your own infrastructure.

Today we are excited to share with you our [Docker toolset for production](http://help.cloud66.com/building-your-stack/introduction-to-docker-deployments). A complete product suite to make it easy to benefit from containers in a production environment.

But first let’s have a look at some of the hurdles of getting containers into production:

## Using containers for development is easy; not so much in production.
[Docker](https://www.docker.com/) (and Linux containers in general) can improve many aspects of software development. They bring:

- Consistency between development and production
- Packaged runtime dependencies
- Decoupling from underlying hardware, virtualisation and OS for many applications
- Speed in build and deployment

However running a container-based stack in production is not easy. Here is what you need:

- A complete build process to build container images based on your code deterministically and continuously. 
- A private Docker image repository to keep your images versioned and linked back to your code commits
- An orchestration engine to rollout those images into containers on your servers, monitor them and manage their lifecycle with each new deployment, as well as take care of scaling of containers and servers.
- A network that exposes containers’ network internally or to the outside world and connects the containers together across the cluster.
- [“Service Discovery”](http://en.wikipedia.org/wiki/Service_discovery) to allow different parts of your application find each other inside your containers.
- Load Balancing for internal and external services provided by the containers
- Production-ready database within the cluster with backups and replication.
- Log collection across all containers and servers

Cloud 66 provides all of these to you in one simple to use tool including web UI, command line and API.

Let’s see how: 

## Cloud 66 Docker production toolset
Cloud 66 support for Docker, includes a complete set of tools you need to run your applications in containers and in production. Here is a summary:

- **BuildGrid**: a hosted Docker image building service to build Docker images directly from your git code repository.
- **Docker Image Repository**: BuildGrid comes with a Docker image repository to hold and distribute your built container images.
- **Deployment Engine**: A cloud deployment system compatible with all major cloud providers (AWS, Rackspace, DigitalOcean, Linode, Azure, Google Cloud and OpenStack) to fire up, build and configure servers under your own cloud account.
- **Orchestration Engine**: A container management system to rollout containers to your servers, distribute and balance external and internal traffic to them, manage their lifecycle during deployments and take care of scaling servers and containers.
- **Data services**: Build, deployment and management of databases  on your servers, compatible with MySQL, PostgreSQL, MongoDB, Redis and ElasticSearch. Including off-site managed backups and replication.
- **ContainerNet**: A private and secure network between all containers, databases and hosts across your infrastructure with an automatically updated DHCP and DNS fully integrated with the Orchestration Engine and Deployment Engine.
- **Logging**: A framework to collect logs from all running containers that can be sent to SysLog or a 3rd party vendor for processing.
- **Monitoring**: A server and container monitoring system to watch vital signs on servers and containers and produce alerts.
- **Automatic upgrades**: Monitoring of OS and components in your infrastructure to produce warnings and automatic upgrades when needed.
- **Security and ACL**: Provisioning, management and monitoring of firewalls, brute force login attempts and user access permissions to all servers for your team members.

{<1>}![Cloud 66 Overview](http://cdn.cloud66.com/images/blog/cloud66_overview_5.png)

Details about some of the these components are below. For those interested in technical details, please feel free to visit [our documentation](http://help.cloud66.com/building-your-stack/introduction-to-docker-deployments).

## From Code to Docker images with BuildGrid
BuildGrid is a hosted Docker image building service that fetches your code from any git repository and uses your own Dockerfile to build a Docker image.

The first step in using containers in production is introducing them into your development process. 

This involves building Docker images from your code and based on your requirements. If you have this process in place and generate Docker images from your code on a build server or in a [CI system like Codeship](https://codeship.com), you can simply point Cloud 66 to your image repository. Alternatively you can use BuildGrid to build your images for you from your code.

BuildGrid can be configured to rebuild new images every time code is committed into the repository, to achieve full continuous delivery. 

BuildGrid comes with a private Docker image repository and a web UI which links code commits to an image, successful and failed builds and build logs. Images can be pulled from this repository to your development workstation for debugging and testing purposes.

## ContainerNet

ContainerNet is a private and secure network connecting all of your containers and hosts in your cluster. It comes with built-in DHCP and DNS (ElasticDNS) services that are aware of your entire stack and deployments and reflect any changes in any of those across your stack automatically.

ContainerNet is backed by [Weave](http://weave.works/) which brings a native-like network interface to the containers requiring no code changes, is highly performant and secure and scales very well.

_Note: ElasticDNS is the name of our DNS service which is available from all containers and is fully integrated with BuildGrid and our deployment engine._

{<2>}![Cloud 66 ContainerNet](http://cdn.cloud66.com/images/blog/cloud66-docker.png)
#### ContainerNet and ElasticDNS

Every service deployment updates the DNS servers across the cluster to have the correct containers for each container and host. 

ElasticDNS is capable of returning the best candidate for each DNS query: round robin, closest or same version as the caller.

This is the simplest way to use Service Discovery without forcing any code change on your side.

## Log Collection
Logs from all containers are collected into specific but customisable folders on each host and can be configured to be sent to hosted log providers like [Logentries](https://logentries.com/) or your own Syslog. To take it further you can use Docker’s stats API for better logging and stats gathering with [Logentries’ recent full integration](https://logentries.com/logentries-releases-logging-container-docker-1-5-stats-api/).

## Extras
All stacks deployed with Cloud 66 also benefit from the following:

- Server-level dynamic [firewall configuration and security](http://help.cloud66.com/managing-your-stack/stack-network-settings).
- OS monitoring and automatic upgrades on your own schedule.
- Fine grained [team access control](http://help.cloud66.com/account-management/team-accounts) for each stack and server.
- Webhooks and API allows you integrate container and deployments with your existing scripts and systems.

# Summary

The Cloud 66 platform manages thousands of servers across 76 data centres in 8 cloud providers for hundreds of small and large companies. Thousands of developers rely on Cloud 66 every day to build, deploy and manage their applications on their servers. 

We’d love to help your engineering team be more productive and your company move faster by making use of Docker in production easier!

Starting with [Docker on Cloud 66](http://help.cloud66.com/building-your-stack/introduction-to-docker-deployments) is very easy. [Try it for free](http://www.cloud66.com/)!
