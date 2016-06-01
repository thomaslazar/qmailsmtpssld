# qmailsmtpssld
A NetBSD `rc.d` start script for running qmail-smdpd with sslserver.

This script is useful for the approximately two other people on this planet that run qmail from `pkgsrc` on NetBSD 
and need to have a second instance of `qmail-smtpd` running with ssl support on port `465`.

# pkgsrc dependencies
-   [./net/ucspi-ssl](http://pkgsrc.se/net/ucspi-ssl) provides sslserver binary 
-   [./mail/qmail-run](http://pkgsrc.se/mail/qmail-run) provides qmailsendd and other scripts needed to run qmail on netbsd

# usage 

1. copy script into `/etc/rc.d/`
2. add `qmailsmtpssld=YES` to `/etc/rc.conf`
3. provide ssl cert. script assumes `/var/qmail/control/servercert.pem` as location
4. run `/etc/rc.d/qmailsmtpssld start` to start

New qmail instance should be available on port `465`
    
# rc.conf options
- `qmailsmtpssld_postenv`: Point `CERTFILE` to the location of your cert.
   Default value is `QMAILQUEUE=/usr/pkg/bin/qmail-queue CERTFILE=/var/qmail/control/servercert.pem KEYFILE= DHFILE= "`.
- `qmailsmtpssld_tcpport`: Sets the port for sslserver to use. Default value is `465`

#  disclaimer 
I do not pretend to understand exactly how the NetBSD `rc.d` System is working, o I do not take any responsibility if this script kills your system or mauls a loved one.  