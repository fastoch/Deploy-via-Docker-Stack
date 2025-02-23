# Deploy to a VPS via Docker Stack (Nov 2024)

src = https://www.youtube.com/watch?v=fuZoxuBiL9o

---

# Why not use Docker Compose?

When it comes to redeploying my applications, I used to manually SSH into my VPS, and run the `docker compose up` command.  
This method works but is not exactly the best developer experience, especially when compared to using platforms such as Vercel, or Netlify.  

Not only is this a bad developer experience, but because of the way that Docker Compose works, it also comes with some undesired side effects.  
The most major of them is that, when you redeploy your application stack using the `docker compose up` command, it can cause downtime.  

Because when Docker Compose redeploys, it begins by shutting down your already running services, before attempting to deploy the upgraded ones.  
So if there's a problem with your new application code or configuration, then these services won't be able to start back up, which will cause your app to have an outage.  

Additionally, by needing to ssh in and copy over the compose.yaml file in order to redeploy, I find this prevents me from being able to ship fast.  
Instead of this manual process, I'd rather have a solution that allows me to easily ship remotely through either my local machine or via **CI/CD**.  

However, rather than using one of the platforms that provide such a service, I did some research and found a solution.  
A solution that not only solves my issue with Docker Compose, but also allows me to use the same Docker compose file I already have set up.  

That solution is **Docker Stack**, which has quickly become my favorite way to deploy my apps to a VPS.  

# How does Docker Stack work?

Docker Stack allows you to deploy your Docker compose files on a node that has **Docker Swarm** mode enabled.  
Which is much better suited for production services compared to Docker Compose.  

It has support for many features that are important when it comes to running a production-grade application, such as:
- Blue/Green Deployments
- Rolling Releases
- Secure Secrets
- Service Rollbacks
- Clustering

Not only this, but when combined with **Docker Context**, I'm able to remotely manage and deploy multiple VPS instances from my own workstation.  
All in a **secure** and **fast** way.  

Let's say I want to make a change to an existing Web App Service Stack by adding in a **Valkey** instance.  
This Web app is running on a VPS and is deployed via Docker Stack.  

All I need to do is edit my docker-compose.yaml file and add in the following lines:
```yaml
valkey:
  image: "valkey/valkey:8"
  volumes:
    - valkey: /data
```
- The first line defines a new service named "valkey"
- The second one specifies that this service should use the Valkey image version 8 from the Docker Hub repository
- The third and fourth lines create a named volume called "valkey" and mounts it to the /data directory inside the container.

Then, in order to deploy this, I can run the `docker stack deploy` command, passing in the docker-compose file that I want to use, and the name of my stack.
```bash
docker stack deploy -c ./docker-compose.yaml <stackName>
```

The `docker stack deploy -c` command is used to deploy a stack of services to a Docker swarm.  
Here's how it works:
- The `-c` flag is short for `--compose-file` and is used to specify the path to a Compose file.
- The command syntax is `docker stack deploy -c <path-to-compose-file> <stack-name>`

After deployment, you can check the status of your services using:
```bash
docker service ls
```

---

## Side note about Valkey

Valkey is an **open-source**, high-performance, in-memory key-value datastore that serves as a **successor to Redis**.   
It functions as a **distributed database**, cache, and message broker with optional durability.  
Valkey was created in **2024** as a fork of Redis 7.2.4 in **response to Redis Ltd.'s switch to proprietary licensing**.  

---

# Other benefits

Besides being able to deploy and redeploy my application services on a remote VPS from my local machine, I'm also able to manage  
and monitor my application from my local machine as well, such as:
- being able to view the different services logs
- adding secrets securely

I've also managed to set up Docker Stack to work with my CI/CD pipeline using **GitHub actions**.  
Meaning whenever I push a code change to the main branch of my repo, it'll automatically deploy my entire stack.  

# How difficult is it to get set up?

It's actually pretty simple, and we'll see how to deploy a simple Web application on a VPS.  
- Open VS Code
- Run `git clone https://github.com/dreamsofcode-io/zenstats.git`

If we open the compose.base.yaml file, we'll see that we have 2 distinct services:
- the web application
- a postgres database

  





@5/28
---
EOF
