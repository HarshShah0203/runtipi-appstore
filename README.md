# Homedex app store for Runtipi

A Runtipi app store with one app: [Homedex](https://github.com/HarshShah0203/homedex), a read-only inventory of the services, hosts, ports, routes, certificates, domains and changes in your homelab.

The official Runtipi store no longer accepts new apps, so Homedex is published here by its author.

## Add this store to Runtipi

Runtipi 4.7.0 or newer (the app uses the native `docker-compose.yml` format).

1. In Runtipi, open **Settings > App Stores > Add appstore**.
2. Appstore name: `Homedex`. Appstore URL: `https://github.com/HarshShah0203/runtipi-appstore`.
3. Open the **App Store**, find **Homedex**, fill in the admin password and install.

## What the app installs

- `homedex`: `ghcr.io/harshshah0203/homedex`, read-only root filesystem, all capabilities dropped, `no-new-privileges`, data in `${APP_DATA_DIR}/data`.
- `docker-socket-proxy`: `tecnativa/docker-socket-proxy:v0.4.2`, the only container that mounts `/var/run/docker.sock` (read only). It allows GET on containers, images, networks, info and version and refuses every write (`POST=0`). It publishes no port and is not on the shared Runtipi network; only Homedex can reach it, at `tcp://docker-socket-proxy:2375`.

Runtipi makes every app's data folder world-writable (`chmod -R a+rwx`) on each start. That is how Homedex, which runs as UID 65532, can write to it. Homedex 0.2.3 and newer put the key that encrypts source credentials back to owner-only as they start, but the inventory database stays readable to other users on the Runtipi host, so keep shell access to the host limited to people you trust.

## Support

Issues: https://github.com/HarshShah0203/homedex/issues

## License

MIT, same as Homedex.
