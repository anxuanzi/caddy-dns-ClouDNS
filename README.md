ClouDNS module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with ClouDNS.

## Caddy module name

```
dns.providers.cloudns
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name": "cloudns",
				"auth_id": "CLOUDNS_AUTH_ID",
                // or sub auth id
                "sub_auth_id": "CLOUDNS_SUB_AUTH_ID",
				"auth_password": "CLOUDNS_AUTH_PASSWORD"
			}
		}
	}
}
```

or with the Caddyfile:

```
# globally
{
	acme_dns cloudns {
        auth_id "<auth_id>"
	    sub_auth_id "<sub_auth_id>"
	    auth_password "<auth_password>"
	}
}
```

```
# one site
tls {
	dns cloudns {
        auth_id "<auth_id>"
	    sub_auth_id "<sub_auth_id>"
	    auth_password "<auth_password>"
	}
}
```
