---
tags:
  - programming
  - tools
---

I was curious about how many people (if any) reads this site, but I am also opposed to using Google analytics. After considering the different alternatives (mainly Matomo), I settled on Plausible because it promised [a simple setup using docker](https://github.com/plausible/community-edition) for self-hosting, it doesn't collect individually identifiable information or use cookies (so no need for cookie banners or GDPR headache, and it offers the basic analytics that I wanted (the number of views for each page.) 

Setting it up was very easy using the provided [Docker image](https://github.com/plausible/community-edition), but it necessitated a bit of tweaking for making it work with Caddy as a reverse proxy. 
# Setting up the Plausible Instance

# Prerequisites
To start, you'll need:
* A website for which you want analytics (duh).
* A server to host your Plausible instance. I use a virtual private server (VPS) from OVH, but any will do. You will need to know its public IP address, and have Docker and the `docker-compose` plugin installed on it.
* A domain or subdomain for the Plausible instance. If you already have a domain name for your website, you can set up a subdomain for Plausible, e.g. have your website accessible at `https://tastyrecipes.com` and your analytics at `https://plausible.tastyrecipes.com`. We'll see in a minute how to set this up. 

## Setting up the DNS Zone
Create an A record pointing to your server's IP address in your DNS configuration file, e.g.:
```
plausible        IN A     12.34.56.78.9
```

The modification can take some time to propagate so if you're impatient like me and want to be able to test your setup immediately, you should ideally do that a day in advance.
## Setting up Plausible on the Server
Log into your server vis SSH, and clone the [`plausible-community`](https://github.com/plausible/community-edition) repo:
```
git clone https://github.com/plausible/community-edition.git
```

Replace the values in `plausible-conf.env`:
```
# put the URL of your plausible instance
BASE_URL=plausible.tastyrecipes.com
# generate the secret key with `openssl rand -base64 48`
SECRET_KEY_BASE=GLVzDZW04FzuS1gMcmBRVhwgd4Gu9YmSl/k/TqfTUXti7FLBd7aflXeQDdwCj6Cz
```

That's it, the plausible instance is ready to run! But for it to be accessible and enforce HTTPS, it's better to set up a reverse proxy.
## Setting up the HTTP Server
The Plausible repository's docker setup includes imanges for reverse proxy. The reverse proxys sits between your Plausible server and clients, and improves security and performance, for instance by enforcing to use the more secure HTTPS protocol on all requests. To run your plausible instance and the provided reverse proxy through docker, you can run:
```
docker compose -f docker-compose.yml -f reverse-proxy/docker-compose.caddy-gen.yml up -d
```

If everything worked correctly, you should be able to access your Plausible instance at the address you specified.

 For some reason the provided reverse proxy didn't work for me, and I found that managing it through docker added an unnecessary layer of complexity, so I simply set one by hand on my VPS.

Apache and Nginx are the 2 most popular reverse proxy applications but here the configuration uses by default Caddy, a reverse proxy implemented in Go and that promises to make the configuration easy and human-readable. I had never heard of it but having had some headaches from Nginx in the past, I was curious about giving it a try.

After [installing Caddy](https://caddyserver.com/docs/install#debian-ubuntu-raspbian), to redirect all requests to the `8000` port, on which the plausible instance listens to, simply create a file named `Caddyfile` with the following content:
```
plausible.tastyrecipes.com {
	reverse_proxy localhost:8000
}
```

and launch the caddy server from the directory where the `Caddyfile` is:
```
caddy start
```

I must say that I was delighted to find that I was impressed by Caddy: it delivered on its promise of a human-readable configuration format, automatic SSL certificate management and HTTPS, etc.
When I was using nginx, I had endless headaches, pasting entire configuration from Stackoverflow that I didn't understand or spending way too long reading documentation. I'm sure Nginx has other benefits, but for this simple use case, Caddy did the job perfectly.
I think I will use it forward, I might even try to host this website (currently on netlify) on the same server. The only downside is that since its userbase is smaller, so you'll find less answers to questions online.

Note: if your subdomain's DNS entry is not yet propagated, Caddy will not be able to generate the SSL certificate, so the Plausible instance will be unreachable. If you  still want to test that plausible is running correctly, you can serve the backend over HTTP by putting in your `Caddyfile`:
```
http://123.45.67.8 {
	reverse_proxy localhost:8000
}
```

You can then access it by entering the IP address in your browser. Don't create users/password with this connection because it's not secured. 

# Use Plausible on your website
## Insert the JS script in your website's code

Once your plausible instance is up and running, time to connect your website to it.
![](assets/images/plausible_new_website.png)

It gives you a snippet to paste into your website's code. If you're using Jekyll, simply add it to `header.html` or any include or layout that gets rendered on all pages of your website.

To keep things clean, you can create variables in `_config.yml` and use them in the `head.html` template:
`_config.yml`
```
analytics:
  site_id: "tastyrecipes.com"
  plausible_url: "https://plausible.tastyrecipes.com"
```

`head.html`
```
{% if site.analytics.site_id && site.analytics.plausible_url %}
	 <script defer data-domain="{{site.analytics.site_id}}" src="{{site.analytics.plausible_url}}/js/script.js"></script>
{% endif %}
```
## Enjoy your Analytics!
![](assets/images/plausible_dashboard.png)

