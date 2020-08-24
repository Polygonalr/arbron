# arbron

A service designed to automate the querying of [VirusTotal](https://www.virustotal.com) for assessments on file hashes. In this case, assessments refer to if the hash in question can be detected by Symantec, and the MD5 translation if it isn't already a MD5 hash and it exists.

Also has shady devices to circumvent the API rate limits which is probably totally a violation of ToS.

## Usage

Before running the service, one would need to generate at least one API key by signing up for a VirusTotal account. Put the API keys in a newline-delimited text file called `keys.txt`.

A `docker-compose.yml` has already been written for one's convenience. Just set up [Docker Compose](https://docs.docker.com/compose/) and run:

```bash
docker-compose up --build
```

Alternatively, refer to `docker-compose.yml` on how to orchestrate this service yourself.

## Services

Read the READMEs of each individual service for their options and any special instructions in running them.

- [`queryer`](https://git.octalorca.me/sombra/arbron/queryer): The API queryer, with key rotation.
- [`cache`](https://git.octalorca.me/sombra/arbron/cache): A cache service to avoid repeating requests with `queryer`.
- [`router`](https://git.octalorca.me/sombra/arbron/router): A HTTP-RPC router-proxy to proxy requests to the main querying pipeline. Otherwise known as the API.
- [`reports`](https://git.octalorca.me/sombra/arbron/reports): A service to generate an Excel sheet report of the supplied assessments.
- [`frontend`](https://git.octalorca.me/sombra/arbron/frontend): The web frontend.
