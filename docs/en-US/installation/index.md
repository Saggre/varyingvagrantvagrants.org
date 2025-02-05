---
category: 2. Getting Started
order: 1
title: Installation
description: VVV can be installed with git by cloning the main VVV repo into a local directory or by downloading a zip file. Start VVV with 'vagrant up'.
permalink: /docs/en-US/installation/
---

First make sure you have all the necessary software installed for VVV to run:

[Vagrant](https://www.vagrantup.com/downloads.html){: .btn target="_blank"}
[Git](https://git-scm.com/downloads){: .btn target="_blank"}{: .btn target="_blank"}

You will also need to install/use one of these vagrant providers:

{% tabs platform %}

{% tab platform Windows %}
[VirtualBox](https://www.virtualbox.org/wiki/Downloads){: .btn target="_blank"}
[Hyper-V](hyper-v.md){: .btn target="_blank"}

Windows users with Docker installed or Hyper-V turned on should use [Hyper-V](hyper-v.md). VirtualBox can be unreliable when Hyper-V is turned on.

{% endtab %}

{% tab platform MacOS (Intel) %}
[VirtualBox](https://www.virtualbox.org/wiki/Downloads){: .btn target="_blank"}
[Parallels Business/Pro*](https://www.parallels.com/){: .btn target="_blank"}

For Parallels you will also need to install the `vagrant-parallels` plugin.

{% endtab %}

{% tab platform MacOS (Arm/M1/M2) %}
[Parallels Business/Pro*](https://www.parallels.com/){: .btn target="_blank"}
[❕ VirtualBox](#){: .btn.disabled}

For Parallels you will also need to install the `vagrant-parallels` plugin.

### Can I Use VirtualBox on Apple Silicon?

No. VirtualBox does not support Apple Silicon, and the technical preview for Arm is years away from being usable. We do not recommend attempting to use the technical preview and we guarantee failure. This may change in the mid to far future ( eta 2025/2026 ).

Note that installing it inside Windows is unlikely to work, and would require a Parallels installation to install Windows anyway.

### Can I Use Docker?

Officially no, there have been efforts to get Docker working but they have been years in the making and are highly experimental with caveats. The only reliable solution on Apple Silicon is Parallels Pro/Business. For more information check the pull requests on GitHub.

{% endtab %}

{% tab platform Linux %}
[VirtualBox](https://www.virtualbox.org/wiki/Downloads){: .btn target="_blank"}
{% endtab %}

{% endtabs %}


Reboot your computer after installing the above software.

## Installing VVV

We're going to install VVV to a `vvv-local` folder in your home directory. First, grab a copy of VVV using `git`. Open a terminal or a command prompt, and enter the following command:

{% tabs installcommand %}

{% tab installcommand MacOS/Linux %}

In a terminal:

```sh
git clone -b stable https://github.com/Varying-Vagrant-Vagrants/VVV.git ~/vvv-local
cd ~/vvv-local
vagrant plugin install --local
```

{% endtab %}

{% tab installcommand Windows %}

In an elevated/admin command prompt:

```powershell
git clone -b stable https://github.com/Varying-Vagrant-Vagrants/VVV.git %systemdrive%%homepath%/vvv-local
cd %systemdrive%%homepath%/vvv-local
vagrant plugin install --local
```

This should have created a `vvv-local` folder in your users main folder, e.g. `C:\Users\myusername\` alongside the documents/pictures/videos/etc folders.

{% endtab %}
{% endtabs %}

Alternatively you can download a zip file from github but we strongly recommend against this though, as it makes updating VVV _much_ harder. If you did this, skip the first commmand.

At this point you might want to adjust the `config/config.yml` file before VVV creates the local developer environment. This is your opportunity to do so. You might do this in order to change the provider vagrant uses to Hyper-V instead of VirtualBox, or to provision additional sites the first time the VM is created to save time.

## Starting VVV

Start VVV by opening a terminal, changing to the VVV folder, and running `vagrant up`. For example:

{% tabs startcommand %}
{% tab startcommand MacOS/Linux %}

```sh
cd ~/vvv-local
vagrant up
```

{% endtab %}
{% tab startcommand Windows %}

```powershell
cd %systemdrive%%homepath%/vvv-local
vagrant up
```

{% endtab %}
{% endtabs %}

The first time you run `vagrant up` may take longer while it installs PHP and other tools. When finished it will show a teddy bear and a VVV logo that look like this:

```sh
    default:
    default:   ✧ ▄▀▀▀▄▄▄▄▄▄▄▀▀▀▄ ✧  Thanks for  __ __ __ __
    default:    ✧█▒▒░░░░░░░░░▒▒█    using       \ V\ V\ V /
    default:  ✧   █░░█░░░░░█░░█ ✧                \_/\_/\_/
    default:   ▄▄  █░░░▀█▀░░░█  ▄▄✧
    default:  █░░█ ▀▄░░░░░░░▄▀ █░░█ Vagrant Up has finished! Visit http://vvv.test
    default: ──────────────────────────────────────────────────────────────────────
```

You will find a dashboard at [http://vvv.test](http://vvv.test), and your websites will be in the `www` subfolder.
