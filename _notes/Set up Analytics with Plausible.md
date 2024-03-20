I was curious about how many people (if any) reads this site, but I am also opposed to use Google analytics. After considering the different alternatives (mainly Matomo), I settled on Plausible because it promised [a simple setup using docker](https://github.com/plausible/community-edition) for self-hosting, it doesn't collect individually identifiable information or use cookies (so no need for cookie banners or GDPR headache, and it offers the basic analytics that I wanted (the number of views for each page.) Here is how I set it up.

What you'll need is:
* A website for which you want analytics  (duh), for instance `https://tastyrecipes.com`
* A server to host your Plausible instance. I use a virtual private server (VPS) from OVH, but any will do. You will need to know its public IP address, and have Docker and the `docker-compose` plugin installed on it.
* A domain or subdomain for the Plausible instance (e.g. `https://plausible.tastyrecipes.com`). We'll see in a minute how to set this up. 

# Setting up the Plausible Instance
## Clone the Plausible-community Repository on your server
Log into your server, and clone the plausible-community repo:
```
git clone 
```
