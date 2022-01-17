# srs-droplet-template

![](http://ossrs.net/gif/v1/sls.gif?site=github.com&path=/tmpl/vm/droplet/ossrs/srs-droplet-template)
[![](https://github.com/ossrs/srs-droplet-template/actions/workflows/droplet.yml/badge.svg)](https://github.com/ossrs/srs-droplet-template/actions/workflows/droplet.yml)

Deploy SRS to DigitalOcean droplet by GitHub Actions.

## Usage

**Step 1:** Create a **[Personal Access Token](https://cloud.digitalocean.com/account/api/tokens?i=896dc7)**, please
check by [doctl](https://docs.digitalocean.com/reference/doctl/how-to/install/):

```bash
doctl auth init -t PERSONAL_ACCESS_TOKEN
```

**Step 2:** Generate **SSH Private Key** and **SSH Public Key** to access the droplet:

```bash
ssh-keygen -b 2048 -t rsa -f ~/.ssh/id_droplet -q -N ""
```

**Step 3:** Click the [<kbd>Use this template</kbd>](https://github.com/ossrs/srs-droplet-template/generate) to create
your repository, then wait for it to be ready.

> Note: The **Usage** of your new repository will be updated automatically, and please follow the **new Usage** to
> finish the setup.

