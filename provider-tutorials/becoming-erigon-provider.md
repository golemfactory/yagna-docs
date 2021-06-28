# Tutorial for becoming Erigolem provider

{% hint style="info" %}
`Erigolem` is a codename for "Erigon on Golem" project. More information can be found at [Example service - managed Erigon](https://github.com/golemfactory/yagna-docs/tree/master/requestor-tutorials/service-development/service-example-2-managed-erigon.md)
{% endhint %}

Here we describe an [installation script](https://github.com/golemfactory/yagna-service-erigon/blob/master/install_provider.sh) which should make the whole process of becoming an Erigolem provider fun and smooth. The script is prepared for Ubuntu 18.04 or later and should work on other Linux distributions after some modifications.
It's not intended to be run on personal computers because

* It creates a separate user which will run the provider daemon,
* It installs the nginx web server and certbot,
* Optionally, it generates a Let's Encrypt certificate and sets certbot to remind you about certificate renewals.

## Requirements

* Ubuntu 18.04 or later
* Root privileges
* Public IP address or a DNS name
* Ability to open a port for the Erigon service

{% hint style="info" %}
By default nginx's reverse-proxy is listening on the standard Erigon port `8545`. You need to open this port for incoming traffic. If you wish your Erigolem service to be available on a different port number (e.g. because `8454` cannot be opened), you need to edit the installation script.
{% endhint %}

<details>
    <summary><b><i>Example patch changing `8545` to `9999`</i></b></summary>

```diff
diff --git a/install_provider.sh b/install_provider.sh
index 2bb4de9..41ad5e2 100644
--- a/install_provider.sh
+++ b/install_provider.sh
@@ -161,8 +161,8 @@ http {
 
     # example.com
     server {
-        listen                               8545${ERIGON_USE_SSL:+ ssl http2};
-        listen                               [::]:8545${ERIGON_USE_SSL:+ ssl http2};
+        listen                               9999${ERIGON_USE_SSL:+ ssl http2};
+        listen                               [::]:9999${ERIGON_USE_SSL:+ ssl http2};
         server_name                          $ERIGON_HOSTNAME;
 
         ${ERIGON_USE_SSL:+# SSL}
@@ -240,7 +240,7 @@ mkdir -p "${ERIGON_USER_HOME}/.local/share/ya-runtime-erigon"
 
 cat >"${ERIGON_USER_HOME}/.local/share/ya-runtime-erigon/ya-runtime-erigon.json" <<EOF
 {
-  "public_addr": "https://${ERIGON_HOSTNAME}:8545",
+  "public_addr": "https://${ERIGON_HOSTNAME}:9999",
   "data_dir": "${ERIGON_DATADIR}",
   "passwd_tool_path": "htpasswd",
   "passwd_file_path": "/etc/nginx/erigon_htpasswd",

```

---
</details>
## Parameters for the script

Script behavior can be modified by the following environment variables:

| name | default value | description |
| :-------- | ----------------: | :------------- |
| ERIGON_USER | `golem` | OS user the service is running on |
| ERIGON_DATADIR | `/data/erigon` | Erigon data directory. Each chain data is collected in the subdirs |
| ERIGON_HOSTNAME |   | __HAS TO__ be set before running the installation script, e.g. `ERIGON_HOSTNAME=X.erigon.golem.network`  |
| ERIGON_DISABLE_SSL |  | Test this script without nagging letsencrypt services. If not set, (the inverse) `ERIGON_USE_SSL` is set |
| ERIGON_EMAIL |  | Not needed when `ERIGON_DISABLE_SSL` is set. Email address for the certbot to remind of SSL certificate renewal. |

## Running the script

1. **Download the installation script locally**

```bash
curl -sSfL -o install_provider.sh \
   https://raw.githubusercontent.com/golemfactory/yagna-service-erigon/master/install_provider.sh
```

2. **Review and edit the script if needed**

3. **Execute the script**

During the installation you will be asked to:

* Accept Golem's licence terms,
* Provide the name for the provider node,
* Provide the subnet the node will be subscribed to,
* Provide your wallet address,
* Provide the desired price per hour (in GLM).

Example script invocation (__provider values for your environment__ )

```bash
sudo env ERIGON_USER=golem \
         ERIGON_HOSTNAME=ec2-54-74-210-145.eu-west-1.compute.amazonaws.com \
         ERIGON_DATADIR=/data/erigon \
         ERIGON_DISABLE_SSL=y \
     bash install_provider.sh
```

4. **Make sure the port is opened**

It depends on how your machine was provisioned but you might need also to allow ingress connections on the firewall.

```bash
sudo ufw allow 8545/tcp
```

## Check installation

After the successful installation verify that the service is running

```bash
sudo systemctl status golem
```

You can also check the logs of the running service

```bash
sudo journalctl -u golem -e
```
