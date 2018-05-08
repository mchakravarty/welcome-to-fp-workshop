# Preparation for the workshop

Please bring your laptop with the following software pre-installed to the workshop.

## macOS

If you are on macOS High Sierra (10.13) or Sierra (10.12), please [download Haskell for Mac](http://download.haskellformac.com/) and activate the 14 day trial. Haskell for Mac is an IDE that makes it easy to get started with Haskell. You will receive a full license key at the workshop.

If you are on a version of macOS older than 10.12, please [install the Haskell Platform (8.0.2)](https://www.haskell.org/platform/download/8.0.2/Haskell%20Platform%208.0.2%20Full%2064bit-signed.pkg) package. This provides you with a command line compiler.

## Windows

Please [install the Haskell Platform (8.0.2)](https://www.haskell.org/platform/download/8.0.2/HaskellPlatform-8.0.2-a-full-x86_64-setup.exe). (There is also a [32bit version](https://www.haskell.org/platform/download/8.0.2/HaskellPlatform-8.0.2-a-full-i386-setup.exe).)

## Linux

Please [download the Haskell Platform (8.0.2)](https://www.haskell.org/platform/download/8.0.2/haskell-platform-8.0.2-unknown-posix--full-x86_64.tar.gz). (There is also a [32bit version](https://www.haskell.org/platform/download/8.0.2/haskell-platform-8.0.2-unknown-posix--full-i386.tar.gz).)

Install by running:

```
$ tar xf ...downloaded archive...
$ sudo ./install-haskell-platform.sh
```

If you have a system with position independent executables by default (such as Ubuntu 16.10 and above), you should edit the GHC settings file at

```
usr/local/haskell/ghc-8.0.2/lib/ghc-8.0.2/settings
```

and change the "compiler supports -no-pie" flag from "NO" to "YES". (This is relative to your installation location.)

**Alternatively,** you can use your distribution's package manger to install version 8.0.2 of the `haskell-platform` package.

## Editor support (optional)

Here are some *optional* suggestions for improved Haskell support in a variety of editors. You will be able to follow the workshop without installing any of these.

* **Haskell for Mac:** Nothing to do: a Haskell editor is built-in. 
* **Emacs:** [haskell-mode](http://haskell.github.io/haskell-mode/)
* **Vim:** [haskell-vim](https://github.com/neovimhaskell/haskell-vim)
* **Sublime:** [SublimeHaskell](https://packagecontrol.io/packages/SublimeHaskell)
* **Atom:** [Atom-Haskell](https://atom-haskell.github.io)
