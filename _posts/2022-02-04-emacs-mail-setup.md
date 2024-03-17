---
layout: post
title: Emacs Mail Setup with mu4e
date: 2022-02-04
redirect_from: /2022/02/04/emacs-mail-setup-on.html
tags: tooling
---

I've used Emacs off and on since my first year of college. [where it was mandatory](https://cs.wellesley.edu/~anderson/writing/emacs/emacs-intro2.pdf). This probably sucked a fair amount of joy out of the process. I was also primarily SSHing into the school servers to do my email (most people worked in the Linux lab, but this required **walking across campus**, and eww), and didn't figure out I could even customize the GUI until many years later.

In my early twenties I was dating a career LISP programmer who used Emacs for everything, including email. I think gnus was the client of choice, but I don't actually remember. We fought a lot about email and communication via email. Whenever I asked my partner to email me something, I'd get angst about how I didn't understand how much technical and emotional labor it took to start Emacs and send email! This made me feel like the process was really painful and to be avoided at all costs. (I experimented with gnus and rmail a few times and it seemed pretty yucky.)

Early on last year, I decided to figure it out once and for all, and got set up with mu4e and mbsync. This quickly became my email workflow of choice, but required a fair amount of work that needed to be repeated every time I provisioned a new dev environment (and since last year my job involved repeatedly shuffling Windows and Linux partitions to do VR work, this was a pretty frequent occurence).

This was what I ended up doing.

### Install the Software

Getting my email to work required installing a lot of different tools:

* mu, a command line email client and the basis for mu4e. allows me to make sense of my mail directory.
* mbsync, a command line tool that syncs my IMAP server with my local mail directory. I need this to actually grab mail from the server.
* mu4e, the emacs package that acts as an interface to mu.
* emacs itself

I also need an IMAP account to actually grab the mail from. I've been using [Fastmail](http://fastmail.com), which also has a web interface I can fall back to.

### Configuring Mail Syncing

There are other programs to do this. I use mbysnc.

First, I have to install it.

```
sudo apt install isync
```

Then I need to set up a mail folder to receive the incoming mail. The default name is `Maildir`.

```
mkdir ~/Maildir
```

Then I have to configure it. This involves editing a file named `~/.mbsyncrc` .

Mine looks like:

```
# Configure remote IMAP account
IMAPAccount fastmail
Host imap.fastmail.com
Port 993
User cidney@fastmail.com
PassCmd "password here"
SSLType IMAPS
SSLVersions TLSv1.2

IMAPStore fastmail-remote
Account fastmail

# Configure local storage
MaildirStore fastmail-local
Path ~/Maildir/
Inbox ~/Maildir/INBOX

# Configure channels
Channel fastmail
Far :fastmail-remote:
Near :fastmail-local:
Patterns *
Expunge None
CopyArrivalDate yes
Sync All
Create Near
SyncState *
```

All of these properties are documented [here](https://isync.sourceforge.io/mbsync.html).

PassCmd requires a special note. For now I'm reading it from a plain text file; encryption is beyond the scope of this blog post.

Using Fastmail means I can't just use my account password. I have to go in and [create an app password](https://www.fastmail.help/hc/en-us/articles/360058752854) to access my email. 

Now, running

```
mbsync -a
```

from a terminal prompt fetches all of my emails. I can verify this easily by looking at the contents of my `~/Maildir` directory.

### Setting up mu

Now I can set up mu to use the mail directory.

It needs to be installed first. On my operating system, the command is:

```
sudo apt install maildir-utils
```

Then I can initialize it.

```
mu init --maildir=~/Maildir --my-address=cidney@cidneyhamilton.com
```

This will create the initial store.

I can now use mu from the command line to search my emails.

```
mu index
mu find hello
```

All good! Now to set up mu4e

### Installing mu4e

Install from the command line with:

```
sudo apt install mu4e
```

### Configuring Emacs

I include a `mail.el` file in my configuration to handle my mail configuration, though all of these can be added to `init.el` easily.

 First I need to require the mu4e package.

```
(require 'mu4e)
```

In order to get mail with mbysnc via an emacs keybinding, I need to add

```
(setq mu4e-get-mail-command  "mbsync -a")
```

I'm also using some additional configuration parameters borrowed from [Rakhim's tutorial on setting up mu4e on MacOS](https://rakhim.org/fastmail-setup-with-emacs-mu4e-and-mbsync-on-macos/).

```
;; Show addresses in viewed messages
(setq mu4e-view-show-addresses t)

;; Needed for mbsync
(setq mu4e-change-filenames-when-moving t)

;; Set path to the attachments directory
(setq mu4e-attachments-dir "~/Downloads")

;; Set path to the mail directory
(setq mu4e-maildir       "~/Maildir")

;; Set additional folders
;; These are set relative to mu4e-maildir
(setq mu4e-sent-folder   "/Sent")
(setq mu4e-drafts-folder "/Drafts")
(setq mu4e-trash-folder  "/Trash")
```

Now, when I enter `M-x mu4e` in emacs, I launch mu4e and can read my email.

### Sending Mail with MSMTP

Right now I can receive mail, but I can't send it! This will require me to configure SMTP locally to send mail.

I use `msmtp` for this.

```
sudo apt install msmtp
```

Now it needs to be configured. I create a configuration file named `~/.msmtprc`. After I enter my configuration information, it looks like this:

```
defaults
auth on
protocol smtp
tls on

account fastmail
host smtp.fastmail.com
port 465
user cidney@fastmail.com
passwordeval "cat ~/.mbsync-pwd"
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

From here I can relaunch Emacs, open mu4e with `M-x mu4e`, and compose and send a test email to another account to verify that everything works.






