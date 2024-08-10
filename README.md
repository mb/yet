# [yet.wiki](https://yet.wiki)

Collection of single-purpose yet-pages answering simple questions. All pages live under the same subdomain [yet.wiki](https://yet.wiki) reducing the cost and maintainance of setting up such single-purpose websites compared to other [areweyet](https://wiki.mozilla.org/Areweyet).

## Adding new subdomains

Create a new directory with the subdomain you want to use. For example

```bash
mkdir are.we.happy.yet.wiki
```

Add a simple HTML file with the answer look at current examples for inspiration.
Add the subdomain to the [Caddyfile](./Caddyfile).

```Caddyfile
are.we.happy.yet.wiki {
	root * /srv/yet/are.we.happy.yet.wiki
	file_server
	bind 2a03:4000:66:c4a::1
	bind 89.58.41.211
}

```

Make a pull request on [Github](https://github.com/mb/yet) to merge the changes to get them deployed.

## Automated deploy

Currently the webserver hosting yet.wiki is hourly pulling the repository and serving the static content with Caddy.
Cloudflare DNS is configured with a wildcard to return
```
A 89.58.41.211
AAAA 2a03:4000:66:c4a::1
```
Caddy takes care requesting HTTPS certificate for configured subdomains.

## Requesting subdomains

Feel free to reach out to me if you want to leverage a subdomain with a different hoster like Github pages or similar.
