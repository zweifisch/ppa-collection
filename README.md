#!/bin/bash

## install

    install(){
        curl https://raw.githubusercontent.com/zweifisch/ppa-collection/master/README.md \
            | sudo tee /usr/bin/ppa-collection
        sudo chmod +x /usr/bin/ppa-collection
    }

## packages

### cmake

    cmake() {
        sudo add-apt-repository ppa:george-edison55/cmake-3.x
        sudo apt-get update
        sudo apt-get install cmake
    }

### crystal

    crystal(){
        curl http://dist.crystal-lang.org/apt/setup.sh | sudo bash
        sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 09617FD37CC06B54
        echo deb http://dist.crystal-lang.org/apt crystal main \
            | sudo tee /etc/apt/sources.list.d/crystal.list
        sudo apt-get install crystal
    }


### docker

    docker(){
        [ -e /usr/lib/apt/methods/https ] || {
            sudo apt-get update
            sudo apt-get install apt-transport-https
        }
        sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 \
            --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
        echo deb https://get.docker.com/ubuntu docker main \
            | sudo tee /etc/apt/sources.list.d/docker.list
        sudo apt-get update
        sudo apt-get install lxc-docker
    }

### elixir

    elixir(){
        wget http://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb \
            -O /tmp/erlang-solutions.deb && sudo dpkg -i /tmp/erlang-solutions.deb
        sudo apt-get update
        sudo apt-get install elixir
    }

### emacs

    emacs(){
        sudo apt-add-repository -y ppa:adrozdoff/emacs
        sudo apt update
        sudo apt install emacs25
    }

### erlang

    erlang(){
        wget http://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb \
            -O /tmp/erlang-solutions.deb && sudo dpkg -i /tmp/erlang-solutions.deb
        sudo apt-get update
        sudo apt-get install erlang
    }

### firefox

    firefox(){
        sudo add-apt-repository ppa:ubuntu-mozilla-daily/firefox-aurora
        sudo apt-get update
        sudo apt-get install firefox
    }

    remove-firefox() {
        sudo apt-add-repository --remove ppa:ubuntu-mozilla-daily/firefox-aurora
    }

### fish

    fish() {
        sudo apt-add-repository ppa:fish-shell/release-2
        sudo apt-get update
        sudo apt-get install fish
    }

### fsharp

    fsharp() {
        sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
        echo "deb http://download.mono-project.com/repo/debian wheezy main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list
        sudo apt-get update
        sudo apt-get install mono-complete fsharp
    }

### git

    git() {
        sudo add-apt-repository ppa:git-core/ppa
        sudo apt-get update
        sudo apt-get install git
    }

### go

    go() {
        sudo add-apt-repository ppa:gophers/archive
        sudo apt-get update
        sudo apt-get install golang
    }

### java

    java(){
        sudo add-apt-repository ppa:webupd8team/java
        sudo apt-get update
        sudo apt-get install oracle-java7-installer
    }

### kivy

    kivy(){
        sudo add-apt-repository ppa:kivy-team/kivy
        sudo apt-get update
        sudo apt-get install kivy
    }

### mongodb

    mongodb(){
        echo deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen \
            | sudo tee /etc/apt/sources.list.d/mongo.list
        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
        sudo apt-get update
        sudo apt-get install mongodb-10gen
    }

### neo4j

    neo4j(){
        echo deb http://debian.neo4j.org/repo stable \
            | sudo tee /etc/apt/sources.list.d/neo4j.list
        wget -O - http://debian.neo4j.org/neotechnology.gpg.key | sudo apt-key add -
        sudo apt-get update
        sudo apt-get install neo4j
    }

### neovim

    neovim(){
        sudo apt-add-repository ppa:neovim-ppa/unstable
        sudo apt-get update
        sudo apt-get install neovim
    }

### nginx

    nginx(){
        sudo apt-add-repository ppa:nginx/stable
        sudo apt-get update
        sudo apt-get install nginx
    }

### nodejs

    nodejs(){
        sudo apt-add-repository ppa:chris-lea/node.js
        sudo apt-get update
        sudo apt-get install nodejs
    }

### ocaml

    ocaml(){
        sudo add-apt-repository ppa:avsm/ppa
        sudo apt-get update
        sudo apt-get install ocaml ocaml-native-compilers camlp4-extra opam
    }

### phantomjs

    phantomjs(){
        sudo add-apt-repository ppa:tanguy-patte/phantomjs
        sudo apt-get update
        sudo apt-get install phantomjs
    }

### php

    php(){
        sudo add-apt-repository ppa:ondrej/php5
        sudo apt-get update
        sudo apt-get install php5
    }

### postgresql

    postgresql(){
        wget -qO - https://www.postgresql.org/media/keys/ACCC4CF8.asc \
            | sudo apt-key add -
        echo deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main \
            | sudo tee /etc/apt/sources.list.d/postgresql.list
        sudo apt-get update
        sudo apt-get install postgresql
    }

### rabbitmq

    rabbitmq(){
        echo deb http://www.rabbitmq.com/debian/ testing main \
            | sudo tee /etc/apt/sources.list.d/rabbitmq.list
        wget -O - http://www.rabbitmq.com/rabbitmq-signing-key-public.asc \
            | sudo apt-key add -
        sudo apt-get update
        sudo apt-get install rabbitmq-server
    }

### redis

    redis(){
        sudo apt-add-repository ppa:chris-lea/redis-server
        sudo apt-get update
        sudo apt-get install redis-server
    }

### rethinkdb

    rethinkdb(){
        sudo add-apt-repository ppa:rethinkdb/ppa
        sudo apt-get update
        sudo apt-get install rethinkdb
    }

### riak

    riak(){
        echo deb http://apt.basho.com precise main \
            | sudo tee  /etc/apt/sources.list.d/basho.list
        wget -O - http://apt.basho.com/gpg/basho.apt.key | sudo apt-key add -
        sudo apt-get update
        sudo apt-get install riak
    }

### elasticsearch

    elasticsearch(){
        wget -qO - http://packages.elasticsearch.org/GPG-KEY-elasticsearch | sudo apt-key add -
        echo deb http://packages.elasticsearch.org/elasticsearch/1.3/debian stable main \
            | sudo tee /etc/apt/sources.list.d/elasticsearch.list
        sudo apt-get update
        sudo apt-get install elasticsearch
    }

### tmux

    tmux(){
        sudo add-apt-repository ppa:pi-rho/dev
        sudo apt-get update
        sudo apt-get install tmux
    }

### racket

    racket(){
        sudo add-apt-repository ppa:plt/racket
        sudo apt-get update
        sudo apt-get install racket
    }

### rust

    rust(){
        curl -s https://static.rust-lang.org/rustup.sh | sudo sh
    }

### stack

    stack(){
        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 575159689BEFB442
        echo "deb http://download.fpcomplete.com/ubuntu/$(lsb_release -cs) stable main" \
            | sudo tee /etc/apt/sources.list.d/fpco.list
        sudo apt-get update && sudo apt-get install stack -y
    }

### syncthing

    syncthing(){
        curl -s https://syncthing.net/release-key.txt | sudo apt-key add -
        echo deb http://apt.syncthing.net/ syncthing release \
            | sudo tee /etc/apt/sources.list.d/syncthing-release.list
        sudo apt-get update
        sudo apt-get install syncthing
    }

### zeal

    zeal(){
        sudo add-apt-repository ppa:jerzy-kozera/zeal-ppa
        sudo apt-get update
        sudo apt-get install zeal
    }

## update

    update(){
        curl https://raw.githubusercontent.com/zweifisch/ppa-collection/master/README.md \
            | sudo tee /usr/bin/ppa-collection
    }

## usage

    usage(){
        echo "usage:"
        echo
        echo "    $0 <package>"
        echo
        echo "packages:"
        echo
        sed -n 's/^###/   /p' $0
        echo
        echo "update:"
        echo
        echo "    $0 update"
        echo
    }

## main

    if [[ $# = 0 ]]; then
        usage
    else
        $1
    fi

# vim: set ft=shell:
