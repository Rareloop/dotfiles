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
nano /etc/apache2/httpd.conf
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

First, [download & install sublime](https://download.sublimetext.com/Sublime%20Text%20Build%203083.dmg). __Note: Using `brew cask install sublime-text` installed Sublime Text 2, not 3. Didn't seem to have one for 3.__

Then, install [Package Control](https://packagecontrol.io/installation).

Using Package Control, install the following packages:

- All Autocomplete
- Blade Snippets
- Colorsublime
- EditorConfig
- Emmet
- Handlebars
- PHP-Twig
- Sass
- SASS Snippets
- SideBarEnhancements
- SublimeLinter
- SublimeLinter-contrib-eslint
- SublimeLinter-json
- SublimeLinter-phpcs
- Twig

Now, install dependencies for the linters:

**[SublimeLinter-phpcs](https://github.com/SublimeLinter/SublimeLinter-phpcs)**

- [Install PEAR and PECL on Mac OS X](http://jason.pureconcepts.net/2012/10/install-pear-pecl-mac-os-x/)
- `pear install PHP_CodeSniffer`

**[SublimeLinter-eslint](https://github.com/roadhump/SublimeLinter-eslint)**

- `npm install -g eslint`

**[Sublimelinter-scss-lint](https://github.com/attenzione/SublimeLinter-scss-lint)**

- `sudo gem install scss_lint`

**Material Theme**

- Install [Fire Code](https://github.com/tonsky/FiraCode) font.

### Sublime - User Settings

```json
{
    "always_show_minimap_viewport": true,
    "auto_complete_selector": "source, meta.tag - punctuation.definition.tag.begin",
    "bold_folder_labels": true,
    "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
    "ensure_newline_at_eof_on_save": true,
    "folder_exclude_patterns":
    [
        ".git",
        ".hg",
        "CVS",
        ".sass-cache",
    ],
    "font_face": "Fira Code",
    "font_options":
    [
        "gray_antialias"
    ],
    "font_size": 19,
    "ignored_packages":
    [
        "Markdown",
        "Vintage"
    ],
    "indent_guide_options":
    [
        "draw_normal",
        "draw_active"
    ],
    "line_padding_bottom": 3,
    "line_padding_top": 3,
    "overlay_scroll_bars": "enabled",
    "theme": "Material-Theme.sublime-theme",
    "translate_tabs_to_spaces": true,
    "trim_trailing_white_space_on_save": true
}
```

### Sublime - SublimeLinter Settings

```json
{
    "user": {
        "debug": false,
        "delay": 0.25,
        "error_color": "D02000",
        "gutter_theme": "Packages/SublimeLinter/gutter-themes/Default/Default.gutter-theme",
        "gutter_theme_excludes": [],
        "lint_mode": "save only",
        "linters": {
            "eslint": {
                "@disable": false,
                "args": [],
                "excludes": []
            },
            "jshint": {
                "@disable": false,
                "args": [],
                "excludes": []
            },
            "json": {
                "@disable": false,
                "args": [],
                "excludes": [],
                "strict": true
            },
            "php": {
                "@disable": false,
                "args": [],
                "excludes": []
            },
            "phpcs": {
                "@disable": false,
                "args": [],
                "excludes": [],
                "standard": "PSR2"
            },
            "scss": {
                "@disable": false,
                "args": [],
                "exclude-linter": [
                    "SelectorFormat",
                    "NameFormat"
                ],
                "excludes": [],
                "include-linter": ""
            },
            "shellcheck": {
                "@disable": false,
                "args": [],
                "exclude": "",
                "excludes": []
            }
        },
        "mark_style": "outline",
        "no_column_highlights_line": false,
        "passive_warnings": false,
        "paths": {
            "linux": [],
            "osx": [],
            "windows": []
        },
        "python_paths": {
            "linux": [],
            "osx": [],
            "windows": []
        },
        "rc_search_limit": 3,
        "shell_timeout": 10,
        "show_errors_on_save": false,
        "show_marks_in_minimap": true,
        "syntax_map": {
            "html (django)": "html",
            "html (rails)": "html",
            "html 5": "html",
            "php": "html",
            "python django": "python"
        },
        "warning_color": "DDB700",
        "wrap_find": true
    }
}
```

### Launch Sublime from the command line

http://olivierlacan.com/posts/launch-sublime-text-3-from-the-command-line/

For example:

```bash
sublime ./
```

## Rareloop Slack Theme

`#34454E,#263238,#28a9e3,#FFFFFF,#1b2b33,#ffffff,#FFFFFF,#ff6465`

## Thanks to
[Mathias Bynens](http://twitter.com/mathias "Follow @mathias on Twitter") for the [original repo](https://github.com/mathiasbynens/dotfiles) we used to start this guide.
