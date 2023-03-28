# Irssi Setup

Irssi is a client to send messages over irc protocol, it's common on open source development. Follow the step below to
get a configured version of irssi with tor to hide hostname informations on `/whois` command

```console
$ mkdir -p ~/.irssi/certs/
$ change irc.libera.chat to palladium.libera.chat
$ write on /etc/tor/torrc
    MapAddress palladium.libera.chat libera<hash>.onion # get on libera chat official site
$ openssl req -x509 -new -newkey rsa:4096 -sha256 -days 1096 -nodes -out irc.pem -keyout irc.pem
$ /network modify -sasl_mechanism PLAIN -sasl_username <username> -sasl_password <pass> liberachat
$ /server modify -tls_verify -tls_cert ~/.irssi/certs/irc.pem irc.libera.chat 6697
$ /connect liberachat
$ /msg NickServ CERT ADD
$ /disconnect
$ /network modify -sasl_password '' -sasl_mechanism EXTERNAL LiberaChat
$ /ignore -channels * JOINS QUITS
$ /save
$ proxychains4 irssi # execute over proxychains
```