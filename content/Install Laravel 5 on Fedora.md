---
title: "Install Laravel 5 on Fedora"
date: 2018-05-10T13:55:37+08:00
categories: [Laravel]
tags: [Laravel,Fedora]
toc: true
math: true
---
# Prerequisites

1. [Install Apache Web Server](https://developer.fedoraproject.org/start/sw/web-app/apache.html)
2. [Install MariaDB Relational Database Server](https://developer.fedoraproject.org/tech/database/mariadb/about.html)
3. [Install PHP](https://developer.fedoraproject.org/tech/languages/php/php-installation.html)


# Installation

## Install PHP Extensions

{{< highlight sh "noclasses=false" >}}
# Laravel required PHP extensions.
$ sudo dnf install php php-common php-cli php-pdo php-mbstring php-zip php-xml
# Restart Apache
$ sudo systemctl restart httpd
{{< / highlight >}}

## Install Composer

We will need composer to install laravel and it’s dependencies

{{< highlight sh "noclasses=false" >}}
$ curl -sS https://getcomposer.org/installer | php
$ sudo mv composer.phar /usr/local/bin/composer
$ chmod +x /usr/local/bin/composer
$ composer -V
{{< / highlight >}}

## Install laravel installer

{{< highlight sh "noclasses=false" >}}
$ composer global require "laravel/installer"
# Place the ~/.config/composer/vendor/bin directory in your PATH so the laravel
# executable can be located by your system.
$ echo 'export PATH="$PATH:$HOME/.config/composer/vendor/bin"' >> ~/.bashrc
{{< / highlight >}}

Restart Terminal. Now you can create a laravel project with the commands

{{< highlight sh "noclasses=false" >}}
$ laravel new ProjectName
{{< / highlight >}}

## Setup

{{< highlight sh "noclasses=false" >}}
$ cd ProjectName
$ cp .env.example .env
$ nano .env
{{< / highlight >}}

Edit the .env file with DB_* lines with the correct info

{{< highlight sh "noclasses=false" >}}
DB_HOST=localhost
DB_DATABASE=laravel_equals_winning
DB_USERNAME=Chur
DB_PASSWORD=Chur1
{{< / highlight >}}

## Serve

{{< highlight sh "noclasses=false" >}}
$ php artisan serve
# Laravel development server started on http://localhost:PORT/
{{< / highlight >}}

# More Problems
1.`storage`permissions:`775` group:`apache`
2.application key
