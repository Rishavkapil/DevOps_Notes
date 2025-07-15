

By default all the docker data including containers, images, volumes, network and all , these all are stored in `/var/lib/docker`

this directory has limited space , so we can change it to any directory



If docker is newly installed then it will not be present there, so you need to create it in `/etc/docker/daemon.json`
To do that we need to go to 
`/etc/docker/daemon.json`

```
{
  "userns-remap": "default",
  "data-root": "/data/docker-data"
}
```

