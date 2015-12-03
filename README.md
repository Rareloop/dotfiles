# Rareloop Mac Setup

Process to setup a fresh Mac install for development.

## Installation

### Install Homebrew
```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Download this repo
```bash
cd ~/Desktop
curl -L https://github.com/rareloop/dotfiles/archive/master.zip > dotfiles.zip
unzip dotfiles.zip
```

### Install what we need from Homebrew
```bash
~/Desktop/dotfiles-master/.brew
```

### Install what we need from NPM
```bash
~/Desktop/dotfiles-master/.npm
```

### Install some useful native applications
```bash
~/Desktop/dotfiles-master/.cask
```

### Setup some sensible OSX defaults
```bash
~/Desktop/dotfiles-master/.osx
```

### Get ready for Git
Edit `~/Desktop/dotfiles-master/.extra` and edit:

- `GIT_AUTHOR_NAME`
- `GIT_AUTHOR_EMAIL`

### Create an SSH Key
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

### Update Apache to use PHP from Homebrew
```bash
nano /etc/apache/http.conf
```

Look for the line that contains `LoadModule php5_module` and replace with `LoadModule php5_module /usr/local/opt/php56/libexec/apache2/libphp5.so`.

```bash
sudo apachectl -k restart
```

### Install the dotfiles
```bash
source ~/Desktop/dotfiles-master/bootstrap.sh
```

## Extras

### Install custom Terminal theme
- Open Terminal
- Open Preferences
- Goto Profiles tab
- Import `~/Desktop/dotfiles-master/presets/Rareloop.terminal`
- Set as default

### Setup code linting in Sublime Text
- Base setup [TODO]
    - ESLint [TODO]
    - SCSSLint [TODO]
    - PSR4 [TODO]
    - JSON [TODO]

## Thanks to
[Mathias Bynens](http://twitter.com/mathias "Follow @mathias on Twitter") for the [original repo](https://github.com/mathiasbynens/dotfiles) we used to start this guide.
