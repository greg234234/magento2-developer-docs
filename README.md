# Magento 2 Developer Documentation
======================

This is a Magento 2 developer documentation site built with [nanoc](http://nanoc.ws/).

## Building and previewing

You'll need to install the following:

* Ruby 1.9.3, the bundler gem, and all gem dependencies

See our platform-specific instructions below:

### OS X / Linux (recommended)

1. Get Ruby 1.9.3+ by following [the Ruby installation instructions](http://www.ruby-lang.org/en/downloads/). We recommend using [rbenv](https://github.com/sstephenson/rbenv) or [rvm](https://rvm.io).

2. Once you have Ruby, install the bundle gem:

        gem install bundler

3. Then use bundler to install all other gems:

        bundle install
 
### Windows

#### Prereqs

Install git. We recommend [msysgit](http://msysgit.github.com/). Download Git for Windows [here](http://git-scm.com/download/win). 
If msysgit doesn't install, you can install [git for windows](http://code.google.com/p/msysgit/downloads/list?q=full+installer+official+git).
Once installed, follow github's directions:

* Set up git for Windows https://help.github.com/articles/set-up-git#platform-windows (don't download github for windows)
* Generate SSH Keys: https://help.github.com/articles/generating-ssh-keys
* [Add git to your PATH](http://blog.countableset.ch/2012/06/07/adding-git-to-windows-7-path/)

In order to avoid a cert error, you'll want to make sure to clone via ssh, rather than via https.

#### Install Ruby and nanoc

1. Download and run the installer for Ruby 1.9.3 (or higher) from http://rubyinstaller.org/downloads/.
    * Make sure to check the "Add Ruby executables to your PATH" checkbox in the installer.

1. Open the terminal.  
    * Go to the Start menu, type `cmd` into the search bar and hit enter.
    * or go to Start menu > Ruby 1.9.3-p### > Start Command Prompt with Ruby

1. Run `gem install bundler`.

1. Run `bundle` to test bundler installation (should say "Could not locate Gemfile"). 

1. Download and run the "Development Kit" exe from http://rubyinstaller.org/downloads/.

1. Follow the instructions at https://github.com/oneclick/rubyinstaller/wiki/development-kit to install.

1. Open a new cmd prompt, cd into your directory, run `bundle`.  If you did these steps correctly, the bundle will build give a happy message, such as "Your bundle is complete!"

1. Run `rake compile` to generate html in output dir.

#### Configure TortoiseGit for GitHub (optional)
If you want a Windows front-end that allows you to use Github and run related commands, you'll want TortoiseGit.

1.   Install tortoisegit:
http://code.google.com/p/tortoisegit/
1.   Using puttygen (which is installed with TortoiseGit), generate a public/private key pair. Save the public and private keys as files on your local drive.
1.  Paste the public key (as it appears under the **Public key for pasting into...** text area) in the **SSH Keys** section of your github.paypal.com profile.
1. Run Pageant and add your private key to it. This should prevent TortoiseGit from asking for your password. Pageant should always be running in the background.
1.	(Optional?) Point to your private key from tortoisegit settings (Git > Remote > Putty Key).
1.	Use TortoiseGit gitclone to create a local version of the repository. Example:
`git@github.com:magento/magento2-developer-docs.git`
