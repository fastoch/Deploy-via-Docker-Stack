# Deploy to a VPS via Docker Stack

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
- Remote Deployments
- Clustering




@3/28
---
EOF
