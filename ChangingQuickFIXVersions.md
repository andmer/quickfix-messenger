# Introduction #
<wiki:gadget url="https://goo.gl/Uql18" width="728" height="90" border="0" up\_ad\_client="7386150814279344" up\_ad\_slot="5169503048" up\_ad\_keywords="trading stocks fx bonds" />

QuickFIX Messenger is a front-end messaging application built on-top of the [QuickFIX/J](http://www.quickfixj.org) engine.

It is a tool designed for technical individuals working on the Financial Information eXchange ("[FIX](http://fixprotocol.org/)") Protocol. The FIX Protocol is an industry-driven messaging standard for the electronic communication of trade-related messages.

QuickFIX Messenger is ideal for testing different messages and scenarios on FIX infrastructures. It provides a simple graphical user interface (GUI) for constructing and sending FIX messages across a given FIX session.


---





---

# Getting Started #
_Note that this guide requires QuickFIX Messenger version 2.0 or higher._

## Downloading QuickFIX/J ##
Download the binary distribution of the desired QuickFIX/J version from [SourceForge](http://sourceforge.net/projects/quickfixj/files/QuickFIX_J/).

Binary distributions are usually named:
  * `quickfixj-<version>-bin.zip`
  * `quickfixj-<version>.tar.gz`

## Updating the QuickFIX/J Library ##
  1. Extract the distribution package to a desired directory location
  1. Copy `quickfixj-all-<version>.jar`
  1. Paste to the `<qfix-messenger>/lib/` directory
  1. Delete the JAR file of the previous version

## Updating the QuickFIX/J Data Dictionaries ##
  1. Go to `<quickfixj>/etc/`
  1. Copy all `XML` files (`FIX*.xml` and `FIXT*.xml`)
  1. Paste to the `<qfix-messenger>/resources/` directory
  1. Overwrite files when required