# Mail From CLI On Linux

To send an email from the cli it's necessary to configure a mail transfer agent (MTA), for this we'll use the postfix
agent (with a gmail account in mind).

To install the postfix run (debian based distros):

```console
$ sudo apt install postfix
```

on the installation process you'll be asked to input a fully qualified domain name (FQDN), on this step you can ignore
with an empty string and answering 'yes' on the next window frame

Create a new file on `/etc/postfix/sasl/sasl_passwd` and insert the following content:

```
[smtp.gmail.com]:587 [mail-addr]@gmail.com:[password]
```

Switch `[mail-addr]` and `[password]` with the correct value of your account. After that generate a db file (*this file
need to be access only by the root user with the `0600` permission) with the following command:

```console
$ sudo postmap /etc/postfix/sasl/sasl_passwd
```

a new file `sasl_passwd.db` will be generated on the same directory.

Insert the content on the `/etc/postfix/main.cf`:

```
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
smtp_tls_security_level = encrypt
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
```

To fisish restart the service:

```console
$ sudo systemctl restart postfix
```

To send an email, using the sendmail utility:

```console
$ sendmail [address] < msg.txt
```

> The file msg.txt has the following format

```
To: addr@mail.com
From: "Alias" <addr@mail.com>
Date: Mon, 01 Jan 2000 12:00:00 -0300
Subject: Email subject
Cc: addr@mail.com

<message body>
```
