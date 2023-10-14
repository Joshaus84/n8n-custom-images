# Custom images for n8n

See [my blog post on how](https://www.weeumson.com/posts/Persist-n8n-community-nodes-on-docker-through-updates/) to persist n8n custom and community nodes in your docker setups.

Post V1.0 there are a few changes to permissions so pay close attention to where things are getting installed. n8n now runs as the `node` user.

The easiest option is to use the example in 'bwill-nodes-simple' folder - 

```
FROM n8nio/n8n:latest
# Post v1.0:
RUN mkdir ~/.n8n/nodes && cd ~/.n8n/nodes && npm install n8n-nodes-clicksend && npm install .....
```
See migration checklist here: [https://docs.n8n.io/1-0-migration-checklist/](https://docs.n8n.io/1-0-migration-checklist/) 