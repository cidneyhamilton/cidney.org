---
layout: post
title: Emacs Mail Setup with mu4e
date: 2022-02-04
---

I've used Emacs off and on since my first year of college. [where it was mandatory](https://cs.wellesley.edu/~anderson/writing/emacs/emacs-intro2.pdf). This probably sucked a fair amount of joy out of the process. I was also primarily SSHing into the school servers to do my email (most people worked in the Linux lab, but this required **walking across campus**, and eww), and didn't figure out I could even customize the GUI until many years later.

In my early twenties I was dating a career LISP programmer who used Emacs for everything, including email. I think gnus was the client of choice, but I don't actually remember. We fought a lot about email and communication via email. Whenever I asked my partner to email me something, I'd get angst about how I didn't understand how much technical and emotional labor it took to start Emacs and send email! This made me feel like the process was really painful and to be avoided at all costs. (I experimented with gnus and rmail a few times and it seemed pretty yucky.)

Early on last year, I decided to figure it out once and for all, and got set up with mu4e and mbsync. This quickly became my email workflow of choice, but required a fair amount of work that needed to be repeated every time I provisioned a new dev environment (and since last year my job involved repeatedly shuffling Windows and Linux partitions to do VR work, this was a pretty frequent occurence).

This was what I ended up doing.

### Install the Software

Getting my email to work required installing a lot of different small tools:

* mu, a command line email client and the basis for mu4e. allows me to make sense of my mail directory.
* mbsync, a command line tool that syncs my IMAP server with my local mail directory. I need this to actually grab mail from the server.
* mu4e, the emacs package that acts as an interface to mu.

I also need an IMAP account to actually grab the mail from. I've been using [Fastmail](http://fastmail.com), which also has a web interface I can fall back to.

### Configuring Mail Syncing

There are other programs to do this. I use mbysnc.

First, I have to install it.

```
sudo apt install isync
```

Then I have to configure it. This involves editing a file named `~/.mbsyncrc` .

Mine looks like:

```
# First section: remote IMAP account
IMAPAccount fastmail
Host imap.fastmail.com
Port 993
User cidney@fastmail.com
PassCmd "cat ~/.mbsync-fastmail"
SSLType IMAPS
SSLVersions TLSv1.2

IMAPStore fastmail-remote
Account fastmail

# This section describes the local storage
MaildirStore fastmail-local
Path ~/Maildir/
Inbox ~/Maildir/INBOX

# This section a "channel", a connection between remote and local
Channel fastmail
Master :fastmail-remote:
Slave :fastmail-local:
Patterns *
Expunge None
CopyArrivalDate yes
Sync All
Create Slave
SyncState *
```

Configuring the password is a tricky command. For now I'm just reading from another text file. But I can't just use my Fastmail password. I have to go in and create an app password for mail syncing to work.

The password is the tricky part. Fastmail requires me to [create an app password](https://www.fastmail.help/hc/en-us/articles/360058752854) to access my email. I set this up.

Now, running

```
mbysnc -a
```

in the command line fetches all of my emails. I can verify this easily by looking at the contents of my `~/Maildir` directory.

Now I can initialize mu to use the mail directory.

```
mu init --maildir=~/Maildir --my-address=cidney@cidneyhamilton.com
```

I can now use mu from the command line to search my emails.

```
mu index
mu find hello
```

All good! Now to get it configured in Emacs.

### Configuring Emacs

I use a `mail.el` file to hand my mail configuration. First I need to require the mu4e package.

```
(require 'mu4e)
```

In order to get mail with mbysnc via an emacs keybinding, I need to add

```
(setq mu4e-get-mail-command  "mbsync -a")
```

I'm also using some additional configuration parameters borrowed from [Rakhim's tutorial on setting up mu4e on MacOS](https://rakhim.org/fastmail-setup-with-emacs-mu4e-and-mbsync-on-macos/).

### Sending Mail with MSMTP

I also need to be able to send mail with mu4e! This requires setting up SMTP. This is always the tricky part.

I use `msmtp` for this.

```
sudo apt install msmtp
```

Now it needs to be configured. My configuration looks like:

```
defaults
auth on
protocol smtp
tls on

account fastmail
host smtp.fastmail.com
port 465
user cidney@fastmail.com
passwordeval "cat ~/.mbsync-fastmail"
tls_starttls off
from cidney@cidneyhamilton.com

account default : fastmail
```

Finally, I need to update my `mail.el` file for sending mail. First I need to find the path to mstmp (I use `which msmtp`, then I need to specify my address and name.

```
;; Send mail configuration
(setq send-mail-function 'sendmail-send-it
      sendmail-program "/usr/bin/msmtp"
      mail-specify-envelope-from t
      message-sendmail-envelope-from 'header
      mail-envelope-from 'header
						user-mail-address "cidney@cidneyhamilton.com"
						user-full-name    "Cidney Hamilton")
)
```

I start out by sending a test email to another mail server. It works!




