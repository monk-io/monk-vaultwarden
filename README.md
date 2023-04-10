# Vaultwarden & Monk

This repository contains Monk.io template to deploy Vaultwarden & Monk either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

## Prerequisites

- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

## Make sure monkd is running

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

```bash
foo@bar:~$ monk list vaultwarden
✔ Got the list
Type      Template                 Repository  Version  Tags
runnable  vaultwarden/base         local       -        bitwarden, vaultwarden, password, devops
runnable  vaultwarden/vaultwarden  local       -        bitwarden, vaultwarden, password, devops
```

## Deploy Stack

```bash
foo@bar:~$ monk run vaultwarden/stack
? Select which 'vaultwarden/vaultwarden' to run local/vaultwarden/vaultwarden
✔ Starting the run job: local/vaultwarden/vaultwarden... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% vaultwarden/server:latest local
✔ Checking/pulling images DONE
✔ Starting containers DONE
✔ New container local-8662d0970fa4b7a0b7fb4d6465-warden-vaultwarden-monk-warden created DONE
✔ Started local/vaultwarden/vaultwarden
🔩 templates/local/vaultwarden/vaultwarden
 └─🧊 Peer local
    └─🔩 templates/local/vaultwarden/vaultwarden
       └─📦 local-8662d0970fa4b7a0b7fb4d6465-warden-vaultwarden-monk-warden running
          ├─🧩 vaultwarden/server:latest
          └─💾 /var/lib/monkd/volumes/vaultwarden -> /data/

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/vaultwarden/vaultwarden - Inspect logs
        monk shell     local/vaultwarden/vaultwarden - Connect to the container's shell
        monk do        local/vaultwarden/vaultwarden/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Check web gui

`http://<ip>:8084/`

## Check admin web gui

`http://<ip>:8084/admin`

## Variables

The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                   | Description       | Default |
| -------------------------- | ----------------- | ------- |
| vaultwarden_signup_enabled | Signup enable     | true    |
| vault_port                 | Vault Warden port | 8084    |
| vaultwarden_admin_token    | Vault Admin token | monk    |

## Stop, remove and clean up workloads and templates

```bash
monk purge vaultwarden
```
