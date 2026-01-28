# Creating a Droplet for Staging Development

Quick start guide for: 

1. Setting up a new DO droplet for hosting or development/staging.
2. Installing and starting a Docker Environment on the droplet.
3. Setting up automatic deployment actions from GitHub to the droplet.

## Digital Ocean Setup

To begin, we must first create a project and environment within DO.

### Create a New Project

- Start a new project within our Devoted Digital Ocean Team.
- Give the project a meaningful, unique name related to the customer or site name.
- Match the repo name, if possible.

### Create a Droplet

Within the project, create a new droplet.

For most small projects or staging environments, choose the following settings:

#### Typical Droplet Settings
| Field | Setting | Notes |
|---|---|---|
|Region|New York|Or choose a location close to the client|
|Image|Ubuntu|Latest LTS Version|
|Droplet Type|Basic / Shared CPU|
|CPU Options|Regular SSD|
|Size|Select the smallest option appropriate for the project; you can always upsize it later.|Previously, we've needed at least a 2GB CPU to run a basic LAMP `docker-compose` environment|
|Backups|Off|See details below.|
|Authentication|SSH Key|
|Additional Options|Enable only if necessary.|
|Hostname|Match the repo name if possible. Append `-dev` for development/staging servers or `-prod` for production. |

**Backup Notes:** typically we leave automated backups off until content entry
begins. Database backups are automatically created during the development
process (db exports for local dev, Tugboat, etc). During this phase, frequent
backups (typically daily) are a byproduct of the work being done, making
automated backups somewhat redundant. Since automated backups incur a cost, we
typically leave them off until necessary. Once content entry begins, we enable
automated backups and leave them on until launch (or forever, if we are hosting
the project).

[Droplet Features/Plan Details from DO Docs](https://docs.digitalocean.com/products/droplets/details/features/)

### Configure Firewall

- Go to your Droplet's dashboard, then `Networking > Firewall`
- Use the existing Devoted firewall config where possible.

## Initial Server Setup

See also [Digital Ocean's Initial Setup Guide for Ubuntu](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu)

1. Open the DO console for the droplet or ssh from your machine.
2. Create a user for the project: `adduser projectuser`
3. Grant admin privileges to the project user: `usermod -aG sudo projectuser`
4. Enable SSH for the project user (copy the config from root): `rsync --archive --chown=projectuser:projectuser ~/.ssh /home/projectuser`
5. Exit the root SSH session and open a new one using the project user you just created.
6. Verify if Docker is installed: `which docker`
7. Install Docker if it is not installed: [DO Guide to Install Docker on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)

## Create Backup Directories

In the home directory for the project user you just created, create the
following directories:

`mkdir directory_name`

| Directory | Purpose |
|---|---|
|`backup_assets`|Creating and storing zip archives of the project's image/file uploads (for example, the `wp-content/uploads` directory in WordPress|
|`backup_db`|Storing database backups / sql dumps|

These directories will be accessed by 1) tools that setup the local dev environment and 2) Tugboat preview instances.

## Clone the Repo to the Droplet

1. First verify an SSH key doesn't already exist. Look for files beginning with:
   `~/.ssh/id_` in the new user home directory you created earlier.
1. If there's no public key (likely not for a new user), generate a new one:
   `ssh-keygen`. Follow the prompts and accept the default filename. This will
   be our *deploy key* that allows the server to pull from the repository. We'll
   create a different key for GitHub Actions later.
1. Copy the contents of the public key you just created `cat .ssh/id_whatever.pub`*

> <i>*Key may begin with `id_rsa` or `id_ed25519`. See [ssh-keygen on Wikipedia](https://en.wikipedia.org/wiki/Ssh-keygen) for details.</i>

4. Open your repository settings in a browser window and go to `Deploy Keys` under `Security`.
5. Add a new deploy key:
  - Give the key a meaningful title that indicates the project name and server type: `ProjectName on DO Droplet`.
  - Paste the contents of the public key into they `Key` field
  - Ensure `Allow write access` is *unchecked*: we only want the server to be able to _read_ from the repo, not write to it.
6. Back in the Droplet terminal, clone the repo: `git clone git@github.com:user_or_org_name/repo.git`
7. Recreate any necessary files excluded by `.gitignore`, such as `.env`.

## Initial Start of Docker Environment on Droplet

You'll likely need to add the newly-created user to the `docker` group before
you can run `docker` commands. See [Manage Docker as a non-root
user](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user).

This error indicates the user lacks permission to run Docker:

> ``` permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "[some_location_or_image]": dial unix /var/run/docker.sock: connect: permission denied ```

1. Create the `docker` group if it does not already exist: `sudo groupadd docker`.
1. Add your user to the `docker` group: `sudo usermod -aG docker $USER`.
1. Log out/in, or reboot the Droplet. You may need to use the DO Console to reboot.
1. After reboot, test with `docker run hello-world`.
1. Switch to the project directory and run `docker compose up -d` to start the docker environment.
1. Run build commands (if any) such as `docker exec container_name npm install` or `docker exec container_name composer install` — refer to your project's documentation.
1. Verify the project is visible at the port Docker is serving the site (likely `:8000`).
1. For WordPress, follow the setup/install process _or_ import an existing database (via `docker exec` or phpMyAdmin).

## Setup Deployment Action

We'll use SSH in a [GitHub Action](https://docs.github.com/en/actions) to
connect to the Droplet and pull repo updates automatically. To do that, we must
first create repository secrets that can be used by the action. One of those
secrets is _another_ ssh key that allows the action to connect to the server.
Using two keys will prevent further damage if one key is compromised.

### Create the Action SSH Key

We'll follow mostly the same process as generating our deploy key above:

1. On the server, run `ssh-keygen`.
1. When generating the key, prepend the default name with `_action`.
1. Add the *public* part of the pair to authorized_keys: `cat .ssh/id_whatever_action.pub >> .ssh/authorized_keys`

> *Important*: ensure you use the `>>` operator to cat to `authorized_keys`,
> which will append to the end of file and not overwrite.

4. Copy the *private* part of the pair `cat .ssh/id_whatever_action` and paste
   it into Repository Secrets (more details below).

### Add the Credentials to the Repository Secrets

Open your repository's secrets settings by going to:

> Settings > Secrets & Variables > Actions > Repository Secrets > New repository secret

...and create the following secrets:

| Secret | Name Suggestion* | Value |
|---|---|---|
| Host | `DO_DEV_HOST` | Domain or IP Address of the Droplet |
| Port | `DO_DEV_PORT` | Port on the Droplet to connect to via SSH, typically `22` |
| Username | `DO_DEV_USERNAME` | Username you created above |
| Key | `DO_DEV_SSH_KEY` | *Private* key you created above ending in `_actions` |

> <i>*Secret Names:<br />
Name suggestions shown in example for a development server, ie "<u>D</u>igital <u>O</u>cean Dev ______".<br />
If cloning a starter project, check for an existing deployment action with existing names.<br />
The `devoted-wp-start` uses `DO_DROPLET_`</i>

### Create the Action

Next, configure the [action](https://docs.github.com/en/actions) that tells GitHub what to do.

> The `devoted-wp-start` project should already have this file created, so you
> can likely skip this step if you've cloned that repo to start your project.

1. Create a `.github/workflows` directory in your project if it does not already exist.
2. Create a new YAML file in this directory with a name that describes what the
   action will do. For example, `deploy-dev.yml` to deploy to a development
   server.
3. Configure your action to deploy on pushes to the `dev` branch, or whichever
   branch is appropriate for your task. See [GitHub Action Workflow
   Syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
   for details on how to configure a GitHub Action.
4. Use the [Appleboy SSH Action](https://github.com/appleboy/ssh-action) to
   connect to the Droplet.
5. Pass the Appleboy action the repository secrets you created above.
6. Pass the Appleboy action a script to run once the ssh connection has been
   made. See the example below.

```
script: |
    cd repo_name
    git checkout dev
    git pull origin dev
    docker compose down
    docker compose up -d
```

What the above example script for deployment does:

1. Go to the project directory.
2. Checkout the branch you want to deploy and pull it.
3. Stop and restart Docker.

## Optional: Configure Port Availability & HTTPS

To use a domain name, we must configure a reverse proxy for the port Docker is
serving the site (for example, `:8000`), and ensure the site is being served
over HTTPS. The [Caddy](https://caddyserver.com/) webserver easily automates
HTTPS and a reverse proxy.

⚠️ Important: if using WordPress, ensure the "site url" fields configured during
set up match the domain configured in Caddy!

1. Follow Caddy's [Ubuntu Installation Instructions](https://caddyserver.com/docs/install#debian-ubuntu-raspbian).
2. Create a `Caddyfile` in the project directory using a text editor of your
   choice, ie `nano Caddyfile`. [Caddyfile
   Docs](https://caddyserver.com/docs/caddyfile-tutorial)
3. In the `Caddyfile`, enter the following configuration:

```
example.com {
    reverse_proxy :8000
}
```

<i>*Replace `example.com` with your domain and replace `:8000` with whatever port your Docker service is using.</i>

4. Start the webserver in the background and verify it's working: `caddy start`
   or `sudo caddy start`
5. If you make a change to the `Caddyfile` or change config via command line,
   don't forget to [reload the
   server](https://caddyserver.com/docs/command-line#caddy-reload) with `caddy
   reload`.

[Full List of Caddy Commands](https://caddyserver.com/docs/command-line)

### HTTPS

Caddy will automatically provision a TLS certificate and serve over HTTPS. See
Caddy's [Automatic HTTPS Docs](https://caddyserver.com/docs/automatic-https) for
details and caveats.

Additional configuration may be needed for Wildcard certificates for subdomains.
[Example](https://caddyserver.com/docs/caddyfile/patterns#wildcard-certificates)
