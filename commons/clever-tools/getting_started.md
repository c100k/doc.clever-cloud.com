---
title: Getting started with Clever Cloud CLI
position: 1
shortdesc: Installing and using the Clever Cloud CLI tool
tags:
- cli-setup
keywords:
- cli
- clever-tools
---

In addition to the Clever Cloud console, you can manage your addons and
applications from the command line with Clever Tools.

## Installing Clever Tools

Clever Tools is available on Windows, GNU/Linux and MacOS.

### MacOS

Clever Tools is packaged using [homebrew](https://brew.sh):

    brew install CleverCloud/tap/clever-tools

If you don't want to use `brew`, a pre-compiled version is available: [clever-tools-latest_macos.tar.gz](https://clever-tools.cellar.services.clever-cloud.com/releases/latest/clever-tools-latest_macos.tar.gz).
You need to put both files (`clever` and `nodegit.node`) in your `PATH` to use the application.

#### Autocompletion

Clever Tools comes with a comprehensive auto-completion system. The brew package installs it automatically (for `bash` and `zsh`). Make sure `bash-completions` or `zsh-completions` are properly set up.

    # In ~/.bash_profile
    . /usr/local/etc/bash_completion

    # In ~/.zshrc
    fpath=(/usr/local/share/zsh-completions $fpath)

### Windows

Clever Tools is packaged using [chocolatey](https://chocolatey.org):

    choco install clever-tools

If you don't want to use `chocolatey`, a pre-compiled version is available: [clever-tools-latest_win.zip](https://clever-tools.cellar.services.clever-cloud.com/releases/latest/clever-tools-latest_win.zip).
You need to add both files (`clever.exe` and `nodegit.node`) to your `PATH` to use the application.

### GNU/Linux

#### Archlinux

The package is available on the AUR: [clever-tools-bin](https://aur.archlinux.org/packages/clever-tools-bin/)

#### Other distributions

A pre-compiled version is available: [clever-tools-latest_linux.tar.gz](https://clever-tools.cellar.services.clever-cloud.com/releases/latest/clever-tools-latest_linux.tar.gz).
You need to add both files (`clever` and `nodegit.node`) to your `PATH`
(you can put them in `~/.local/bin` for instance)
to use the application.

#### Autocompletion

Clever Tools comes with a comprehensive auto-completion system.

    # for bash
    clever --bash-autocomplete-script $(which clever) | sudo tee /usr/share/bash-completion/completions/clever

    # for zsh
    clever --zsh-autocomplete-script $(which clever) | sudo tee /usr/share/zsh/site-functions

### Usage via global npm install

We no longer support the usage and installation of Clever Tools via a global npm install.
Please follow the installation instructions for your platform (see above) and make sure to uninstall the npm version with this:

    npm uninstall -g clever-tools

## Linking your account

Once you have installed Clever Tools, the next step is to link your account:

    clever login

This will open a login page in your browser, and will give you identification
tokens. Copy them and paste them in the `clever login` prompt.

## Linking an existing application

If you have an already existing application, you can start managing it with
Clever Tools.

    # First, go to your local repository
    cd /path/to/your/application

    # Then, link it to the Clever Cloud application
    clever link <app_id>

    # You can also use the application name (make sure to specify the
    # organization name if your application is in an organization.
    clever link --org <org_name> <app_name>

    # Unlink an application
    clever unlink <app_id>

<div class="panel panel-warning">
  <div class="panel-heading">
     <h4>Notes on `.clever.json`</h4>
  </div>
  <div class="panel-body">
    <div>
      Once you have linked an application, clever-tools will create a Json configuration file named `.clever.json` at the root of the directory.
    </div>
    <div>This file can be commited safely, others team members working on this repository will not have to link the application again.</div>
    <div>This configuration file contains the AppID, so keep this in mind if you publish it on a public repository.</div>
  </div>
</div>
<br>
## Deploying new code

After having written new code, you can deploy it to Clever Cloud

    # Will git push your code to Clever Cloud and display logs
    clever deploy

    # Will open your application
    clever open
