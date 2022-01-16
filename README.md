# srs-droplet-template

![](http://ossrs.net/gif/v1/sls.gif?site=github.com&path=/k8s/droplet/ossrs/srs-droplet-template)
[![](https://github.com/ossrs/srs-droplet-template/actions/workflows/droplet.yml/badge.svg)](https://github.com/ossrs/srs-droplet-template/actions/workflows/droplet.yml)

Deploy SRS to DigitalOcean droplet by GitHub Actions.

## Usage

**Step 1:** Create a **[Personal Access Token](https://cloud.digitalocean.com/account/api/tokens?i=896dc7)**, please
check by [doctl](https://docs.digitalocean.com/reference/doctl/how-to/install/):

```bash
doctl auth init -t PERSONAL_ACCESS_TOKEN
```

**Step 2:** Click the [<kbd>Use this template</kbd>](https://github.com/ossrs/srs-droplet-template/generate) to create your
repository, then wait for your repository to be ready(the **Usage** will changed automatically), and follow the new
usage to finish the setup.

