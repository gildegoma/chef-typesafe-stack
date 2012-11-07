Description
===========

*The [Typesafe Stack](http://typesafe.com/stack) is an integrated distribution that includes the Scala programming language, Akka event-driven middleware, and the Play web framework, along with a robust suite of development tools.*

The **default** recipe of this Chef cookbook will
 * Configure the APT or YUM repository provided by TypeSafe company
 * Install the meta-package **typesafe-stack** that includes supported versions of [sbt](https://github.com/harrah/xsbt) and [giter8](https://github.com/n8han/giter8). 

**Note:** On Debian/APT-based platorm, the repository public key is installed in more "standard way" compared to [Debian/Ubuntu installation guidelines](http://typesafe.com/stack/download) from TypeSafe. (I expect that TypeSafe will in near future make its apt-repo public key available for usual HTTP download... and drop the manual installation-step of repo-deb-build-0002.deb package)

Requirements
============

* depends on opscode/apt cookbook 1.4.0+ because of **[COOK-921** (the apt-repository public key file is bundled in cookbook, not HTTP-fetched from a remote server)
* **Attention:** Integration with opscode-apt cookbook 1.4.8+ requires at least Chef 0.10.10+ because of **COOK-1435**. See opscode-cookbooks/apt@4c8d03f6afc22eca0b1ffb7389e61aec9a16666b

Attributes
==========

TODO (if needed)

Usage
=====

TODO 

Quality Assurance
=================

Version 0.1.0 has been validated on Ubuntu 12.10 64-bit (for apt)  and on CentOS 6.4 64-bit (for yum)

Credits
=======

The creation of this cookbook has been influenced by:
 * https://github.com/garrettux/scala-sbt-cookbook/blob/master/recipes/default.rb 
 * https://github.com/opyate/typesafe-stack-cookbook/blob/master/recipes/default.rb 

