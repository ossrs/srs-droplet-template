# %NAME%

![](http://ossrs.net/gif/v1/sls.gif?site=github.com&path=/tmpl/vm/droplet/ossrs/%NAME%)
[![](https://github.com/ossrs/%NAME%/actions/workflows/droplet.yml/badge.svg)](https://github.com/ossrs/%NAME%/actions/workflows/droplet.yml)

Deploy SRS to DigitalOcean droplet.

## Usage

- [x] Step 1: Create a **Personal Access Token**
- [x] Step 2: Generate **SSH Private Key** and **SSH Public Key**
- [ ] Step 3: Set the **secrets**
- [ ] Step 4: Click **Run workflow**

Please follow the detail steps bellow.

**Step 1:** Create a **[Personal Access Token](https://cloud.digitalocean.com/account/api/tokens?i=896dc7)**, please check by:

```bash
doctl auth init -t PERSONAL_ACCESS_TOKEN
```

**Step 2:** Generate **SSH Private Key** and **SSH Public Key** to access the droplet:

```bash
ssh-keygen -b 2048 -t rsa -f ~/.ssh/id_droplet -q -N ""
```

**Step 3:** Set the [secrets](https://github.com/ossrs/%NAME%/settings/secrets/actions):

* `DIGITALOCEAN_ACCESS_TOKEN` is the **Personal Access Token**.
* `DIGITALOCEAN_SSH_PRIVATEKEY` is the **SSH Private Key**, by `cat ~/.ssh/id_droplet`
* `DIGITALOCEAN_SSH_PUBLICKEY` is the **SSH Public Key**, by `cat ~/.ssh/id_droplet.pub`

**Step 4:** Click [Run workflow](https://github.com/ossrs/%NAME%/actions/workflows/droplet.yml) to restart it manually,
for example, if your droplet PublicIPv4 is `81.70.125.89`:

* Website is http://81.70.125.89
* Publish RTMP to rtmp://81.70.125.89/live/livestream
* Play RTMP from rtmp://81.70.125.89/live/livestream
* Play HTTP-FLV from [http://81.70.125.89/live/livestream.flv](http://81.70.125.89/players/srs_player.html?stream=livestream.flv&&autostart=true)
* Play HLS from [http://81.70.125.89/live/livestream.m3u8](http://81.70.125.89/players/srs_player.html?stream=livestream.m3u8&&autostart=true)

Try to modify the [README.md](README.md), then push to your repository, your droplet will be updated automatically.

## HTTPS by SSL files (Optional)

For HTTPS, you need a SSL cert from CA, such as [ssls.com](https://www.ssls.com/), or the actions will generate a
self-signed SSL cert.

Please set the bellow [secrets](https://github.com/ossrs/%NAME%/settings/secrets/actions),
then click the [Run workflow](https://github.com/ossrs/%NAME%/actions/workflows/droplet.yml) manually:

* `DIGITALOCEAN_SSL_KEY` is the SSL key file, by `cat server.key`
* `DIGITALOCEAN_SSL_CERT` is the SSL cert file, by `cat server.crt`

> Note: This is optional, and the workflow will generate a self-signed if the secrets are not assigned.

> For self-signed SSL certificate, please click the blank of page, and enter the magic word `thisisunsafe` without
> space, please read [Command to Trust a Certificate in Chrome](https://www.youtube.com/watch?v=7J3vSN3pCjI)

> If you got a domain name, please setup the DNS zone with the droplet IP.

> Note: Other proxy servers also work well with SRS, for example,
> [Nginx](https://github.com/ossrs/srs/issues/2881#nginx-proxy) or
> [CaddyServer](https://github.com/ossrs/srs/issues/2881#caddy-proxy).

## Resources

The resources created by the [GitHub Actions](https://github.com/ossrs/%NAME%/actions):

A ssh-key with name `srs-key`:

```bash
doctl compute ssh-key list |grep srs-key
```

A droplet with name `srs-server`:

```bash
doctl compute droplet get srs-server
```

To remove all resources:

```bash
doctl compute droplet delete srs-server -f
doctl compute ssh-key delete $(doctl compute ssh-key list --no-header |grep srs-key |awk '{print $1}') -f
```

