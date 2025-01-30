---
title: Advanced (low-level) Settings guide
sidebar_position: 7
---

:::info

Cet article parle de AdGuard pour Windows, un bloqueur de contenus multifonctionnel qui protège votre appareil au niveau du système. Pour voir comment cela fonctionne, [téléchargez l'application AdGuard](https://agrd.io/download-kb-adblock)

:::

Previously known as low-level settings, Advanced Settings mostly contain options that go beyond the average user competence and aren't applied in everyday use. AdGuard for Windows is designed to work without ever having to change any of them, but they will provide additional features in some corner cases or when solving an uncommon problem.

:::caution

Mindlessly changing *Advanced Settings* can potentially cause problems with the performance of AdGuard, may break the Internet connection or compromise your security and privacy. You should only make changes to these settings if you are sure of what you are doing or if our support team has asked you to do so.

:::

## How to reach Advanced Settings

To go to *Advanced settings*, in the main windows click *Settings → General Settings* and scroll down to *Advanced Settings*. Alternatively, select *Advanced → Advanced settings...* in the tray menu.

## Advanced Settings

Once you open Advanced Settings, you will be presented with the following options:

### Block TCP Fast Open

If enabled, AdGuard will block TCP Fast Open in the Edge browser. To apply settings, you need to restart the browser.

### Use Encrypted Client Hello

Every encrypted Internet connection has an unencrypted part. This is the very first packet which contains the name of the server you are connecting to. La technologie Encrypted Client Hello est censée résoudre ce problème et chiffrer ce dernier morceau d'information non chiffrée. To benefit from it, enable the *Use Encrypted Client Hello* option. It uses a local DNS proxy to look for the ECH configuration for the domain. If it is found, Client Hello packet will be encrypted.

### Check websites' certificate transparency

Vérifie l'authenticité de tous les certificats du domaine en fonction de la politique de transparence des certificats Chrome. If the certificate does not comply with the Chrome Certificate Transparency Policy, AdGuard will not filter the website. Chrome, in turn, will block it.

### Enable SSL/TLS certificate revocation checks

Once enabled, this option runs asynchronous OCSP checks to check whether the website’s SSL/TLS certificate is revoked.

If the OCSP check completes within the minimum timeout, AdGuard will immediately apply the result: block the connection if the certificate is revoked or establish a connection if the certificate is valid.

If the verification takes too long, AdGuard will establish a connection and continue checking in the background. If the certificate is revoked, current and future connections to the domain will be blocked.

### Show AdGuard VPN in Settings

Enabling this option allows you to display the AdGuard VPN tab in Settings for easy opening of the app and the product's website.

### Exclude app from filtering by entering the full path

If you want AdGuard not to filter any specific application, specify the full path to them and the apps will be excluded from filtering. Separate different paths by semicolons.

### Enable AdGuard pop-up notifications

Enable this feature to see AdGuard pop-up notifications. Ils n'apparaissent pas trop souvent et contiennent uniquement des informations importantes. You can also use the tray menu to recall the last pop-up notification.

### Automatically intercept filter subscription URLs

Enable this feature if you want AdGuard to automatically intercept filter subscription URLs (i.e. `abp:subscribe` and alike) and to open a custom filter installation dialog.

### Filter HTTP/3

If this option is enabled, AdGuard will filter requests sent over HTTP/3 in addition to other request types.

### Use redirect driver mode

If this option is enabled, AdGuard intercepts all the traffic and redirects it to the local proxy server for further filtering.

Otherwise, AdGuard will filter all the traffic on the fly, without redirection. In this case, the system will consider AdGuard to be the sole application that connects to the Internet (other applications are routed through it). The downside is that it will make the system Firewall less effective. The upside is that this approach works a little bit faster.

### Open main window at system start-up

Enable this option to make the main AdGuard window open after the system is loaded. Notez que cela n'affecte pas le lancement ou non du service de filtrage réel, ce paramètre se situe dans *Paramètres → Mode général*.

### Enable filtering at system start-up

Starting from v7.12, by default, AdGuard's service does not filter traffic after OS startup if the option Launch AdGuard at system start-up is disabled. In other words, the AdGuard's service is started in “idle” mode. Enable this option to make AdGuard filter traffic even if the app is not launched.

:::note

Before v7.12, the AdGuard service started in filtering mode by default (even if the *Launch AdGuard at system start-up* was disabled). If you were satisfied with the old behavior, enable this option.

:::

### Filter localhost

If you want AdGuard to filter loopback connections, check the box. This option will always be on if you have AdGuard VPN installed, because otherwise it won't be able to work.

### Exclude specified IP ranges from filtering

If you don't want AdGuard to filter particular subnets, enable this feature and specify the IP ranges in the CIDR notation (e.g. 98.51.100.14/24) in the **IP ranges excluded from filtering** section below.

### Enable HAR writing

This option should be enabled **only for debugging purposes**. Cocher la case à cocher fera en sorte qu'AdGuard crée un fichier au format HAR 1.2 contenant des informations sur toutes les requêtes HTTP filtrées. This file can be analyzed with the Fiddler app. Veuillez noter que cela peut ralentir votre navigation sur le web de manière significative.

### Add an extra space to the plain HTTP request

Adds extra space between the HTTP method and the URL and removes space after the "Host:" field to avoid deep packet inspection. For instance, the request

`GET /foo/bar/ HTTP/1.1
Host: example.org`

will be converted to

`GET /foo/bar/ HTTP/1.1
Host: example.org`

This option is only applied when the *Protect from DPI* Stealth mode option is enabled.

### Adjust size of fragmentation of initial TLS packet

Specifies the size of the TCP packet fragmentation, avoiding deep packet inspection. This option only affects secured (HTTPS) traffic.

If this option is enabled, AdGuard splits the initial TLS packet (the Client Hello packet) into two parts: the first one has the specified length and the second one has the rest, up to the length of the whole initial TLS packet.

Valid values: 1–1500. If invalid size is specified, the value selected by the system will be used. This option is only applied when the *Protect from DPI* Stealth mode option is enabled.

### Plain HTTP request fragment size

Ajuste la taille de la fragmentation de la requête HTTP. This option only affects plain HTTP traffic. If this option is enabled, AdGuard splits the initial packet into two parts: the first one has the specified length and the second one has the rest, up to the length of the whole original packet.

Valid values: 1–1500. If invalid size is specified, the value selected by the system will be used. This option is only applied when the *Protect from DPI* Stealth mode option is enabled.

### Show QUIC

Allows displaying the QUIC protocol records in the filtering log. For blocked requests only.

### Enable TCP keepalive

Periodically sends TCP packets over idle connection to ensure it is alive and to renew NAT timeouts. This option can be useful to bypass the strict network address translation (NAT) settings that some ISPs use.

### TCP keepalive interval

Here you can specify an idle time period, in seconds, before sending a keepalive probe. Si 0 est spécifié, la valeur sélectionnée par le système sera utilisée.

:::note

This setting only works when the *Enable TCP keepalive* option is enabled.

:::

### TCP keepalive timeout

Here you can specify time in seconds before sending another keepalive probe to an unresponsive peer. Si 0 est spécifié, la valeur sélectionnée par le système sera utilisée.

:::note

This setting only works when the *Enable TCP keepalive* option is enabled.

:::

### Bloquer Java

Some websites and web services still support Java Plug-Ins. The API that serves as the basis for Java plug-ins has serious security vulnerabilities. You can disable such plug-ins for security purposes. Nevertheless, even if you decide to use *Block Java* option, JavaScript will still be enabled.

### DNS server timeout period

Here you can specify the time in milliseconds that AdGuard will wait for the response from the selected DNS server before resorting to fallback. If you don’t fill in this field or enter an invalid value, the value of 5000 will be used.

### Use HTTP/3 for DNS-over-HTTPS

Enables HTTP/3 for DNS-over-HTTPS upstreams to accelerate connection if the selected upstream supports this protocol. This means that enabling this option does not guarantee that all DNS requests will be sent via HTTP/3.

### Use fallback DNS upstreams

Normal queries will be redirected to the fallback upstream if all DNS requests to the selected upstreams fail.

### Query DNS upstreams in parallel

All upstreams will be queried in parallel and the first response is returned. Since DNS queries are made in parallel, enabling this feature increases the Internet speed.

### Always respond to failed DNS queries

If address resolving failed on each of the forwarded upstreams, as well as on the fallback domains, then the response to the DNS request will be `SERVFAIL`.

### Enable filtering of secure DNS requests

AdGuard will redirect secure DNS requests to the local DNS proxy, in addition to plain DNS requests.

### Blocking mode for hosts rules

Here you can select the way AdGuard will respond to domains blocked by DNS rules based on [hosts rule syntax](https://adguard-dns.io/kb/general/dns-filtering-syntax/#etc-hosts-syntax).

- Reply with “Refused” error
- Reply with “NxDomain” error
- Reply with a custom IP address

### Blocking mode for adblock-style rules

Here you can select the way AdGuard will respond to domains blocked by DNS rules based on [adblock-style syntax](https://adguard-dns.io/kb/general/dns-filtering-syntax/#adblock-style-syntax).

- Reply with “Refused” error
- Reply with “NxDomain” error
- Reply with a custom IP address

### Custom IPv4 address

If Custom IP address is selected in Blocking mode for hosts rules or Blocking mode for adblock-style rules, this IP address will be returned in response to blocked A requests. If none are specified, AdGuard will reply with the default Refused error.

### Custom IPv6 address

If Custom IP address is selected in Blocking mode for hosts rules or Blocking mode for adblock-style rules, this IP address will be returned in response to blocked AAAA requests. If none are specified, AdGuard will reply with the default "Refused" error.

### Serveurs Fallback

Here you can specify an alternate DNS server to which a DNS request will be rerouted if the main server fails to respond within the timeout period specified in the next section. There are three options to choose from:

- Don’t use fallback servers;
- Use system default servers;
- Use custom servers.

### Block ECH

If enabled, AdGuard strips Encrypted Client Hello parameters from responses.

### Liste des serveurs de secours personnalisés

Si vous souhaitez qu'AdGuard utilise des serveurs de secours personnalisés, listez-les dans cette section, un par ligne.

### Liste des adresses d'amorçage personnalisées

Un amorçage est un serveur DNS intermédiaire utilisé pour obtenir l'adresse IP du serveur DNS sécuritaire que vous avez choisi précédemment dans *Protection DNS*. Un "terme moyen" est nécessaire lors de l'utilisation de protocoles qui désignent l'adresse du serveur par des lettres (comme DNS-over-TLS, par exemple). Dans ce cas, l'amorçage agit comme un traducteur, transformant les lettres en chiffres que votre système peut comprendre.

Par défaut, le résolveur DNS du système est utilisé, et la requête d'amorçage initiale est effectuée via le port 53. Si cela ne vous convient pas, saisissez ici les adresses IP des serveurs DNS qui seront utilisées pour déterminer l'adresse du serveur DNS crypté dans l'ordre de haut en bas. Les adresses IP spécifiées seront appliquées dans l’ordre indiqué. Si vous spécifiez des adresses invalide, ou aucune adresse du tout, les IP du système seront utilisées.

### Exclusions DNS

Toutes les Requêtes DNS vers les domaines énumérés ici seront redirigées vers le serveur DNS Par défaut du système au lieu du serveur DNS spécifié dans les paramètres de l'application. De plus, les règles de blocage DNS ne seront pas appliquées à de telles requêtes.

### Exclusion des noms de réseaux Wi-Fi (SSID) spécifiés du filtrage DNS

La protection DNS n'inclura pas les réseaux Wi-Fi répertoriés dans cette section. Spécifiez les noms de réseaux Wi-Fi (SSID) un par ligne. Cela peut être utile si un réseau Wi-Fi particulier est déjà protégé par AdGuard Home ou un autre système de protection DNS. Dans ce cas, il est inutile de filtrer à nouveau les requêtes DNS.
