# legitDNS systemd updater service

Automatic hourly IP updates for [legitDNS](https://legitdns.com/) dynamic DNS service using systemd.

## Installation

```shell
# Remove example.conf file
rm legitdns.service.d/example.conf

# Create new config with YOUR domain and token
# You can use a more descriptive file name
cat > legitdns.service.d/domain.conf << EOF
[Service]
Environment=DDNS_DOMAIN=insert_your_domain_here
Environment=DDNS_TOKEN=insert_your_token_here
EOF

cp -r legitdns.* /etc/systemd/system/
chown -R root:root /etc/systemd/system/legitdns.*

systemctl daemon-reload
systemctl enable legitdns.timer
systemctl start legitdns.timer
```

## Status

```shell
systemctl status legitdns
```

## Removal

```shell
systemctl stop legitdns.timer
systemctl disable legitdns.timer

rm -rf root:root /etc/systemd/system/legitdns.*
```
