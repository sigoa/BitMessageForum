<table>
<tr>
<td><a href='https://raw.github.com/grant-olson/BitMessageForum/master/screenshots/threads.png'><img src='./screenshots/threads.png' width=233 height=196 /></a><br />View Channel</td>
<td><a href='https://raw.github.com/grant-olson/BitMessageForum/master/screenshots/messages.png'><img src='./screenshots/messages.png' width=205 height=169 /></a><br />Read Thread</td>
</tr>
</table>

# BMF

BitMessageForum allows you to browse and post bitmessages in a
forum-like view in the web browser of your choice, i.e. firefox.

Although BMF is configured to run in your browser, it is designed to
be a local application.  It assumes that if you can talk to your
bitmessage server (e.g. run by pypy as **daemon**), you are fully authorized to read/send/delete any
messages, create new identities, etc.

BMF can be setup as a publically facing website. Although it would be possible to use the software to mirror a channel
via a web interface, this would require some fiddling.

Modify your BMF web pages as root e.g. in  /var/lib/gems/2.3.0/gems/bmf-0.2.2/lib/bmf/views/layout.haml

## Installation

### Prerequisites

#### Software

The following software is required:

* [Ruby](http://www.ruby-lang.org/en/)
* Ruby development toolchain.  `apt-get install ruby-dev build-essential` on Debian-based platforms.
* [PyBitmessage](https://bitmessage.org/wiki/Main_Page)

#### PyBitmessage API configuration

To enable the API for PyBitmessage you must add the following to
the `[bitmessagesettings]` section of keys.dat:

    apienabled = true
    apiport = 8442
    apiinterface = 127.0.0.1
    apiusername = bmf
    apipassword = bmf

### Initial installation

    sudo gem install bmf

### Running the software

    bmf

If you are using different settings for the PyBitmessage server, you
will need to change that on the [settings
page](http://localhost:4567/settings/) or by manually editing
`config/settings.yml`.

### Verifying the software

The gem is signed with
[rubygems-openpgp](https://github.com/grant-olson/rubygems-openpgp).
Assuming you have rubygems-openpgp configured, you can verify the
software:

    gem fetch bmf
    gem verify bmf
    gem install bmf

More details are available at the [rubygems-openpgp project
page](https://github.com/grant-olson/rubygems-openpgp).

### Developers. Run from the source:

### Prerequisites

* a ruby installation capable of building binary extensions. 

* bundler.

Most ruby developers use a tool like [rvm](https://rvm.io/) or
[chruby](https://github.com/postmodern/chruby) to maintain per-user
and per-project versions of ruby.  This prevents you installing dozens
(or possibly hundreds) of ruby gems with arbitrary code system-wide.
It is recommended that you use one of these tools.  After that,
install bundler in the local gemset:

    gem install bundler

If you just want to get things up and running quickly, you
can install ruby and bundler system-wide:

On Debian based systems:

    sudo apt-get install ruby-dev build-essential
    sudo gem install bundler

### Cloning the source and configuring

    git clone https://github.com/grant-olson/BitMessageForum.git
    cd BitMessageForum
    gem install bundler
    bundle install # will need sudo if using system ruby
    ./bmf-dev

### Verifying the source

All stable releases are tagged in git and signed by my OpenPGP key
listed below.  To verify a particular release and run that code:

    master-blaster:BitMessageForum grant$ git verify-tag 0.2.2
    gpg: Signature made Sun Aug  4 17:59:35 2013 EDT using RSA key ID A18A54D6
    gpg: Good signature from "Grant T. Olson (Personal email) <kgo at grant-olson dot net>"
    master-blaster:BitMessageForum grant$ git checkout 0.2.2

### Running PyBitmessage as a daemon

If you find yourself using BMF all the time and don't want to see the
PyBitmessage UI, you can start PyBitmessage as a daemon.

First, add the following to the `[bitmessagesettings]` section of `keys.dat`:

    daemon = true

Next, start PyBitmessage like so:

    nohup python src/bitmessagemain.py &

This will start up PyBitmessage in the background without the QT GUI.

## Contact

Found a bug? [File an issue.](https://github.com/grant-olson/BitMessageForum/issues)

Need help?  Ask on the bmf support channel.

    * Name: bmf_support
    
    * Address: BM-2DBsnPXWVR7PbC5qMEYAdgtaSQnkr5X7ng 

For announcements of new releases and security issues, subscribe to BM-2DABVRoCRtwKZLyVCBZ3n6PuC4n7a4zLsA

Or send me a personal bitmessage: BM-2DAxhHpd2Sez4oQmZu5sEAMJbnNp3yDFCU 

Email me:  kgo at grant-olson dot net.

OpenPGP Key:

    pub   2048R/E3B5806F 2010-01-11 [expires: 2014-01-03]
          Key fingerprint = A530 C31C D762 0D26 E2BA  C384 B6F6 FFD0 E3B5 806F
    uid                  Grant T. Olson (Personal email) <kgo at grant-olson dot net>
    sub   2048R/6A8F7CF6 2010-01-11 [expires: 2014-01-03]
    sub   2048R/A18A54D6 2010-03-01 [expires: 2014-01-03]
    sub   2048R/D53982CE 2010-08-31 [expires: 2014-01-03]
