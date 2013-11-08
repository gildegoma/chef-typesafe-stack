Deprecated!
===========

In 2012, *Typesafe Stack* was the former professional bundle provided by http://typesafe.com. 
After the introduction of **Typesafe Activator** in 2013, these APT and YUM repositories were no longer updated. 
For this reason, I stop using this cookbook and deprecate it in favor to https://github.com/gildegoma/chef-sbt-extras.

Description
===========

*The [Typesafe Stack](http://typesafe.com/stack) is an integrated distribution that includes the Scala programming language, Akka event-driven middleware, and the Play web framework, along with a robust suite of development tools.*

The **default** recipe of this Chef cookbook will

  * Configure the APT or YUM repository provided by TypeSafe company
  * Install the meta-package **typesafe-stack** that includes [sbt](https://github.com/harrah/xsbt) and [giter8](https://github.com/n8han/giter8).

### Notes:

  * Akka and Play are not installed, since TypeSafe recommends to create project on top of these frameworks with giter8 templates available in [@typesafehub](https://github.com/typesafehub) **.g8-suffixed** repositories, like for instance https://github.com/typesafehub/akka-scala-sbt.g8
  * TypeSafe bundles an **adapted version of very nice [sbt-extras](https://github.com/paulp/sbt-extras#readme)**. 
    * Genuine sbt-extras *will figure out the versions of sbt and scala required by the project and download them if necessary.* 
    * *BUT* [typesafe fork](https://github.com/sbt/sbt-launcher-package) disabled the auto-download feature...
    * If you want to install multi-sbt tool ready out of the box, try https://github.com/gildegoma/chef-sbt-extras instead.
  * On Debian/APT-based platorm, the repository public key is installed in a more "usual way" compared to [Debian/Ubuntu installation guidelines](http://typesafe.com/stack/download) from TypeSafe. (I expect that TypeSafe will in near future make its apt-repo public key available for usual HTTP download... and drop the manual installation-step of repo-deb-build-0002.deb package)

Requirements
============

* Depends on **[apt](https://github.com/opscode-cookbooks/apt) >= 1.4.0+** because of [COOK-921](https://github.com/opscode/cookbooks/pull/282) (the apt-repository public key file is bundled in cookbook, not HTTP-fetched from a remote server)
* Depends on **[yum](https://github.com/opscode-cookbooks/yum)**
* Depends on **[java](https://github.com/opscode-cookbooks/java)**
* **Attention:** Integration with opscode-apt cookbook 1.4.8+ requires at least Chef 10.10+ because of [COOK-1435](https://github.com/opscode-cookbooks/apt/commit/4c8d03f6afc22eca0b1ffb7389e61aec9a16666b).
* Conflicts with **[chef-sbt-extras](https://github.com/gildegoma/chef-sbt-extras)**

Attributes
==========

No attribute defined so far

Usage
=====

Include the `typesafe-stack::default` recipe to your run list or inside your cookbook. 

Quality Assurance
=================

Version 0.1.0 has been validated on Ubuntu 12.10 64-bit (for apt)  and on CentOS 6.4 64-bit (for yum)

Known Problems
==============

* [#3](https://github.com/gildegoma/chef-typesafe-stack/issues/3): `sbt` runs by default with following JVM memory parameters `-Xms1536m -Xmx1536m -XX:MaxPermSize=384`. 
 * **workaround:** override JVM memory parameters with `-mem` option (e.g. `sbt -mem 512 ...`)
 * You should expect following error with target host with less than 2048M of RAM:

```
Error occurred during initialization of VM
Could not reserve enough space for object heap
```

 
Contribution and Credits
========================

* Project Home: https://github.com/gildegoma/chef-typesafe-stack
* How to contribute: *Feel free to open issues, fork repo and send pull request (based on a custom branch, not master)!*

Before starting to create this cookbook, I first looked for existing ones, but I did not find exactly what I wished. 
The creation of this cookbook was nevertheless influenced by following similar recipes:

 * https://github.com/garrettux/scala-sbt-cookbook/blob/master/recipes/default.rb 
 * https://github.com/opyate/typesafe-stack-cookbook/blob/master/recipes/default.rb 

