# Vaultwarden & Monk

This repository contains Monk.io template to deploy Vaultwarden & Monk either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

## Prerequisites

- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

### Make sure monkd is running

```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository

```bash
git clone https://github.com/monk-io/vaultwarden
```

## Load Template

```bash
cd vaultwarden
monk load MANIFEST
```

### Let's take a look at the themes I have installed

```bash
foo@bar:~$ monk list vaultwarden
✔ Got the list
Type      Template                      Repository  Version  Tags
group     vaultwarden/stack        local       -        -
runnable  vaultwarden/vaultwarden  local       -        -
```

## Deploy Stack

```bash
foo@bar:~$ monk run vaultwarden/stack
? Select tag to run [local/vaultwarden/stack] on: mnk
✔ Starting the job: local/vaultwarden/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% vaultwarden/server:latest mnk
✔ Checking/pulling images DONE
✔ Started local/vaultwarden/stack

🔩 templates/local/vaultwarden/stack
 └─🧊 Peer mnk
    └─🔩 templates/local/vaultwarden/vaultwarden
       └─📦 ea6c156ea15b2d16212785bc68d53c2f-n-vaultwarden-vaultwarden
          ├─🧩 vaultwarden/server:latest
          ├─💾 /var/lib/monkd/volumes/vaultwarder -> /data/
          └─🔌 open <ip>:8084 (0.0.0.0:8084) -> 80

💡 You can inspect and manage your above stack with these commands:
 monk logs (-f) local/vaultwarden/stack - Inspect logs
 monk shell     local/vaultwarden/stack - Connect to the container's shell
 monk do        local/vaultwarden/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Check web gui

`http://<ip>:8084/`

## Check admin web gui

`http://<ip>:8084/admin`

## Variables

The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                     | Description       | Default |
| ---------------------------- | ----------------- | ------- |
| vaultwarden_signup_enabled | Signup enable     | true    |
| vault_port                  | Vault Warden port | 8084    |
| vaultwarden_admin_token    | Vault Admin token | monk    |

## Stop, remove and clean up workloads and templates

```bash
monk purge vaultwarden
```
