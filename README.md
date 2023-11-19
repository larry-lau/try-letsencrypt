# README
This repo demonstrates using Let's Encrypt to secure app running in docker using 3 different challenge types.

## Base configuration
Create a .env file with the following environment variables for your domain:

```
HOST=whoami.your-domain.com
ACME_EMAIL=contact@your-domain.com
```
## HTTP challenge

```
docker compose -f compose.http.yml up -d
```

## TLS challenge

```
docker compose -f compose.tls.yml up -d
```

## DNS challenge with easydns provider

In order to obtain the key and token value. First, request REST API access in easydns.com > User > Security. You can override the endpoint to use sandbox environment for testing purpose. 

```
DNS_PROVIDER=easydns
EASYDNS_KEY=apixxxxxx.xxxxxxxx
EASYDNS_TOKEN=uxxxxxx.xxxxxxxx
EASYDNS_ENDPOINT=https://rest.easydns.net
```

```
docker compose -f compose.dns.yml up -d
```

## Results

Once the services are up and running, you should find a Json file name acme-{challenge-type}.json in the letsencrypt folder populated with a certificate issued by Let's Encrypt and you should be able to access the whoami service using HTTPS.