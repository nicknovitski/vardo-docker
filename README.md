Vardo
=====

A modern development environment.

Requirements
============

[Vagrant](http://www.vagrantup.com/) and [Ansible](http://www.ansible.com/home)

Installation and Usage
======================

Clone this repo, run `vagrant up`, `ssh`, and `share`.  

Inside the VM, work in the ~/src directories will be synced back to your host machine.

Purpose and Philosophy
======================

Vardo is a project to create a VM for development in general, rather than the development of any specific application.  It expects you to manage _application_ dependencies with Docker, and tries to provide a curated and holistic set of _developer_ dependencies, all of which work over ssh.

For almost as long as I've been pair programming, I've been sweating over how to keep the state of development boxes minimal and consistent, and how to best work remotely.  Vardo is my attempt to create the cloud-era development environment I've dreamt of.

"Yes it's clever, but what does it get me?"
=======================

* [git](http://git-scm.com/)
* [docker](https://www.docker.io/)
* [exuberant ctags](http://ctags.sourceforge.net/): enable meaningful code indexing
  * [automatically run on all git repos](http://tbaggery.com/2011/08/08/effortless-ctags-with-git.html)
* [rbenv](https://github.com/sstephenson/rbenv)
  * [ruby-build](https://github.com/sstephenson/ruby-build): `rbenv install` ruby versions
  * [rbenv-ctags](https://github.com/tpope/rbenv-ctags): automatically run `ctags` on any ruby you install
  * [rbenv-communal-gems](https://github.com/tpope/rbenv-communal-gems): store gems a little more sensibly
  * [rbenv-gem-rehash](https://github.com/sstephenson/rbenv-gem-rehash) automatically run `rbenv rehash` when you install new commands
  * [rbenv-gem-rehash](https://github.com/sstephenson/rbenv-gem-rehash): automatically run `rbenv rehash` when you install new commands
  * [rbenv-binstubs](https://github.com/ianheggie/rbenv-binstubs): transparently uses binstubs so you never need `bundle exec`
  * [rbenv-gem-update](https://github.com/nicknovitski/rbenv-gem-update): always `rbenv install` with the latest rubygems
  * [rbenv-default-gems](https://github.com/sstephenson/rbenv-default-gems)
    * [gem-ctags](https://github.com/tpope/gem-ctags): automatically run ctags on gems as they're installed)
    * [bundler](http://bundler.io/): manage gems
    * [hookup](https://github.com/tpope/hookup): `hookup install` to automatically run `bundle install` when necessary)
    * [rails](https://github.com/rails/rails) you probably know this one
    * [raygun](https://github.com/carbonfive/raygun) the new way to `rails new`
    * [pry](http://pryrepl.org/): advanced alternative to irb
    * [rubocop](https://github.com/bbatsov/rubocop): find offenses in your code
    * [building](https://github.com/CenturyLinkLabs/building): turn any app into a docker container
    * [flay](https://github.com/seattlerb/flay): find similar blocks of code
    * [flog](https://github.com/seattlerb/flog): analyze code for complexity/pain
    * [mutant](https://github.com/mbj/mutant): make sure your tests fail when your code changes
* [nodenv](https://github.com/OiNutter/nodenv): mangage multiple versions of node.js
  * [node-build](https://github.com/OiNutter/node-build): `nodenv install` node versions
  * [node-default-packages](https://github.com/nicknovitski/node-default-packages)
    * [eslint](http://eslint.org/): code analysis
    * [bower](http://bower.io/): front-end package management
    * [yeoman](http://yeoman.io/): webapp scaffolding tool
    * [grunt-cli](http://gruntjs.com/): task runner
    * [testem](https://github.com/airportyh/testem): make testing so easy you'll actually want to do it
* [vim](http://www.vim.org) 
  * [molokai](https://github.com/tomasr/molokai): pretty colors to look at
  * [pathogen](https://github.com/tpope/vim-pathogen): sanitary vim package bundling
    * [sensible](https://github.com/tpope/vim-sensible): sensible defaults
    * [syntastic](https://github.com/scrooloose/syntastic): syntax checking
    * [nerdtree](https://github.com/scrooloose/nerdtree): project navigation
    * [dispatch](https://github.com/tpope/vim-dispatch): background building and testing
    * [fugitive](https://github.com/tpope/vim-fugitive): possibly the best git wrapper of all time
    * [repeat](https://github.com/tpope/vim-repeat): make more things repeatable with `.`
    * [commentary](https://github.com/tpope/vim-commentary): comment things out with `gc`
    * [surround](https://github.com/tpope/vim-surround): master stuff that surrounds other stuff
    * [unimpaired](https://github.com/tpope/vim-unimpaired): make your bracket keys more useful
    * [eunuch](https://github.com/tpope/vim-eunuch): unix commands without leaving the editor
    * [vim-rails](https://github.com/tpope/vim-rails): power tools for rails
    * [vim-bundler](https://github.com/tpope/vim-bundler): some bundler goodies 
    * [abolish](https://github.com/tpope/vim-abolish): easier substitutions for word variants
    * [gitgutter](https://github.com/airblade/vim-gitgutter): adds a column to indicate your current git diff
    * [tagbar](http://majutsushi.github.io/tagbar/): list tags in the current scope
    * [airline](https://github.com/bling/vim-airline): a beautiful status line
    * [tabular](https://github.com/godlygeek/tabular): align things vertically, quickly
    * [vim-move](https://github.com/matze/vim-move): move things up and down
    * [ctrlp.vim](http://kien.github.io/ctrlp.vim): fuzzy finding

"I edit with an IDE"
====================

There are many advantages to that approach, but this project won't help you.
