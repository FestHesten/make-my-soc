# make-my-soc
A quick and easy way to setup and test some Security tools!

It is very much inspired by https://github.com/tomMoulard/make-my-server but is more focused on testing systems and not real production as docker-compose is not the way to run things in the long run!

This has been used for me to learn about containers and docker to create a quck and easy way of testing tooling for my regular work.

In time I hope to create a Kubernetes version of this project but for now and for new users I prefer to keep it docker as it is more beginner friendly.


## Usage

Clone this repo and for each tool you want you will have to create the `.env`. A guide might be included in the readme for each component and if you have problems please create a issue here on github and include as much detail as you can! I will look at things when I have time.

After you have followed the install instructions for each component you want you can simply start it with `docker compose up` or `docker compose up -d` if you dont want to read the debug info. 

## Prerequisites
A little knowlege about docker, some understanding of terminal tools and a will to learn!
I will create guides and explanations at points but I'm not including it from the start. Please create a issue if you need help or want to get more of a tutorial for a specific component! But in general the infromation should be in the documentation of each project so start there! :) 


## Goals
Get a quick and easy way to learn about the different tools in a SOC!

This project includes (or will include) a [SOAR](https://www.tracecat.com/), Ticketing system, [GIT](https://about.gitea.com/), [free text documentation](https://www.getoutline.com/), [DFIR tooling](https://www.dfir-iris.org/) and a CRM system. It is a introduction to anyone who wants to become a security engineer or if you are interested in automation and sysadmin work in any way. It's scoped for a small SOC with a few customers and a need for Customer Relations, Regular tickets and handling alerts from different systems.

If you want to include a system send a PR with some documentation!

Longer term I hope to create a few integrations with Tracecat and a few other systems that gives you a way of ingesting, normalizing and doing automated actions based on workflows and context ingested from all systems. 