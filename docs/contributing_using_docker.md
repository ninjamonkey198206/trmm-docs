# Contributing Using Docker

## Install WSL2

<https://docs.microsoft.com/en-us/windows/wsl/install-win10>

## Install Docker Desktop

<https://www.docker.com/products/docker-desktop>

### Configure Docker

Make sure it doesn't look like this:

![img](images/docker_WSL2_distros_missing.png)

This is better:

![img](images/docker_with_ubuntu-20.04.png)

### Check and Make Sure WSL is v2 and Set Ubuntu as Default

[https://docs.microsoft.com/en-us/windows/wsl/install-win10#set-your-distribution-version-to-wsl-1-or-wsl-2](https://docs.microsoft.com/en-us/windows/wsl/install-win10#set-your-distribution-version-to-wsl-1-or-wsl-2)

![img](images/wls2_upgrade_and_set_default.png)

## Install VSCode Extensions

[Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

[Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

## Connect to WSL and Clone Your Github Fork

![Connect to WSL](images/vscode_wsl_docker_setup1.png)

![Clone Repo](images/vscode_wsl_docker_setup2.png)

## Create .env File

Under .devcontainer duplicate:

```text
.env.example
```

as

```text
.env
```

Customize to your tastes (it doesn't need to be internet configured, just add records in your `hosts` file) eg:

```conf
127.0.0.1    rmm.example.com api.example.com mesh.example.com
```

## Launch your Dev VM in Docker

Right-click `docker-compose.yml` and choose `Compose Up`.

Wait, it'll take a while as docker downloads all the modules and gets running.

## Develop

You're operational!

!!!note
    Self-signed certs are in your dev environment. Navigate to <https://api.example.com> and <https://rmm.example.com> and accept the self signed certs to get rid of errors.

### View MKDocks Live Edits in Browser

Change stuff in `/docs/docs/`

MKDocs is Exposed on Port: 8005

Open: [http://rmm.example.com:8005/](http://rmm.example.com:8005/)

!!!note
    If you add new MKDocs extensions you might need to:<br>
    - docker-compose down.<br>
    - Then delete the `/api/tacticalrmm/env/` folder.<br>
    - Then docker-compose up and it will download / rebuild new extensions.

### View Django Administration

Open: [http://rmm.example.com:8000/admin/](http://rmm.example.com:8000/admin/)
