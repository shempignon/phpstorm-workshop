# Workflow with PhpStorm

The aim of this repo is to help you improve your workflow with JetBrains' PhpStorm. 
Phpstorm is a pretty amazing piece of software, knowing how to use some of its features can help you stay focused on your job (i.e. THE CODE).

PhpStorm is an IDE , meaning that it's much more than a simple text editor, to some extends, it can "understand" your code. Moreover, PhpStorm is shipped with many tools that will ease your workflow - you won't need X to access your DB, Y to manage VCS, Z to communicate with some remote server, it's all in PhpStorm.
   
As every extendable software, if you feel like there's something missing to really achieve the perfect workflow, there's probably a plugin to do the work for you.

P.S.
- This guide exists to help you get quickly started with PhpStorm, and is in no case a replacement for the [**official documentation**][1] (which is great !)
- This guide is open and free, feel free to contribure
- I'm not paid, nor profit in any way, by JetBrains to write this ;)

## Configuration

P.S. This chapter will unfortunately not cover configuration on Mac OS, as I ~~hate~~ don't have access to this OS. Deal with it.


The configuration is split between global and per project items. Let's start with the global configuration.

### Keymap

### Php

#### Remote or Local

Assuming php is installed locally or on some remote server, let's configure PhpStorm. In the `Settings` window :
- In `Language & Frameworks > PHP`
- If the CLI interpreter is empty, click on the `...` button
- Click the green `+` button in the top left corner of the window
- Choose the php binary you want to use (local, remote, or Docker, Vagrant, VM)

Once chosen, you can pick a *language level*, this way you can tell PhpStorm to inspect you code observing 5.6 version rules while your actual interpreter version is 7.1 (or the other way around).

#### Composer

Once you've configured a php interpreter, you can setup Composer by going to `Language & Frameworks > PHP > Composer` in the `Settings` window. You simply need to indicate the interpreter you want to use, the path to the `composer.phar` (a simple click on the link below the field will automatically download it for you) and the path to the project's `composer.json`.

#### Autoloading, namespaces and directories

Configuring the directories can greatly increase indexing performance.

If you project follows PSR-0/4, PhpStorm will prompt you with the following:

:IMAGE_PSR_PROMPT:

You can go a little further by going to `Directories` in the `Settings` window, and selecting in which directories live your project sources, test and which directories you want to ignore.

In the case of a Symfony 3 you would set the `src/` directory as Sources, the `tests/` directory as Tests and the `var/` directory as Excluded. Finally by clicking the little `P̬` button next to the `Test Source Folders` you can set the specific namespace for the `tests/` directory: 'Tests'

:IMAGE_NAMESPACE_OVERRIDE:

#### XDebug

1) XDebug configuration obviously requires you to have it installed:

    ... on Debian / Ubuntu dists
    #: apt-get install php-xdebug
    
2) Then you need to configure the module itself:

    ... in /path/to/xdebug.ini
    zend_extension=/absolute/path/to/xdebug.so
	xdebug.remote_autostart = Off
	xdebug.remote_enable = On
	xdebug.remote_handler =  dbgp
	xdebug.remote_host  =  127.0.0.1
	xdebug.remote_log  = /tmp/xdebug.log
	xdebug.remote_port = 9000
	xdebug.idekey = PHPSTORM

Note that zend_extension need the absolute path to xdebug.so file, this configuration is merely a sample - feel free to tweak to your needs.

3) Setup PhpStorm:
 
Once Xdebug installed, you need to start a web server (Apache, nginx, or even php -S, ...).
In the `Settings` window, go to `Language & Frameworks > PHP > Debug`, click the `Validate` link.
Fill in the "Path to create validation script" with the path the public folder of your application (`/web` in the case of classic Symfony app).
Fill in the "Url to validation script" with the url to your application (don't forget the port if you're using `php -S`).

Click validate, ~~pray~~ everything *should* be go to go.

4 ) Last steps

If you manage to correctly setup XDebug, you are 3 steps away from debugging !

- Install a browser extension to enable debugging on the client side, just search for "Xdebug extension" there are plenty of them. Don't forget to tell it to use the same configuration you set as `xdebug.idekey` as IDEKEY.
- Click the `Start Listening` button in PhpStorm
- Setup some breakpoints in your code, by simply clicking in the left margin.

The first time you run the debugger, you will be prompted to accept or reject incomming connection from the debugger, click `Accept` to process.

If you've successfully followed the step, you should see the debug console popup in your IDE !

5 ) Debugging

While debugging, you can execute a script line after line - you can also evaluate the state of variables at any given time.

:IMAGE_TO_ILLUSTRATE:

### Tests

#### PhpUnit

#### Behat

#### Debugging tests

Unfortunately, this feature is only available on UNIX OS, due to windows shitty management of ENV variables.

### Plugins 

#### Symfony
 
This plugin 

#### Annotations

#### Others

## Version control

### Basics

## Key features

## Vision

In this chapter, I'll explain you my vision of what a good IDE should provide. So this chapter is highly opiniated, you may disagree - IT'S OKAY.

TL;DR: 
- Keep your workflow as clean as possible, remove anything you dont use on a day to day basis,
- Switching between windows is SLOW, I want to have as many tools integrated in my IDE as possible,
- Using the mouse is too much of hassle to be bothered with; keybind everything

### Less windows

### Less Mouse


[1]: https://www.jetbrains.com/phpstorm/documentation/