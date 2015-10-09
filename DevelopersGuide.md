# Introduction #
<wiki:gadget url="https://goo.gl/Uql18" width="728" height="90" border="0" up\_ad\_client="7386150814279344" up\_ad\_slot="5169503048" up\_ad\_keywords="trading stocks fx bonds" />

QuickFIX Messenger is a front-end messaging application built on-top of the [QuickFIX/J](http://www.quickfixj.org) engine.

It is a tool designed for technical individuals working on the Financial Information eXchange ("[FIX](http://fixprotocol.org/)") Protocol. The FIX Protocol is an industry-driven messaging standard for the electronic communication of trade-related messages.

QuickFIX Messenger is ideal for testing different messages and scenarios on FIX infrastructures. It provides a simple graphical user interface (GUI) for constructing and sending FIX messages across a given FIX session.

QuickFIX Messenger is fully open source under the [new BSD License](http://opensource.org/licenses/BSD-3-Clause). Interested contributors may let their intentions known to jramoyo@gmail.com.


---





---

# Development Environment #
## Required Tools ##
  * A modern Java IDE; [Eclipse](http://www.eclipse.org/downloads/) is highly recommended
  * An updated [Java Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
  * A Subversion (SVN) client

## Building the Source Code ##
_This guide assumes that Eclipse (with Subversion plugin) is the chosen IDE._

### Connecting to Subversion ###
  1. Open the SVN Repository perspective
  1. Create a new repository location pointing to https://quickfix-messenger.googlecode.com/svn/
    * Username is your Gmail address
    * Password is your [Google code](https://code.google.com/hosting/settings) generated password

### Checking out from Subversion ###
  1. Traverse to the repository node: trunk > qfix-messenger
  1. Right-click > Checkout
  1. Eclipse should detect that a Java project is being checked-out, accept and proceed

### Executing the Ant script ###
  1. Locate the Ant script (`build.xml`) at the project's root directory
  1. Right-click > Run As > Ant Build
    * This will execute the default Ant target (`clean.deploy`)
    * A different Ant target may be selected from the Ant run configuration (Right-click > Run As > Ant Build...)
  1. The default Ant target will:
    1. Clean all temporary files
    1. Generate classes from XSD
    1. Compile the source code
    1. Create the JAR file
    1. Deploy all files to a working directory
  1. The working directory contains the distributables of the application
    * The default working directory is `deploy`
    * The scripts (_`.sh` for Linux and `.cmd` for Windows_) from this directory can be used to launch the application

## Running from Eclipse ##
  1. Locate the Main class
    * `com.jramoyo.qfixmessenger.QFixMessenger`
  1. Right-click > Run As > Java Application
    * If running for the 1st time, an error message will appear:
      * <font color='red'><code>Usage: QFixMessenger &lt;app cfg file&gt; &lt;quickfix cfg file&gt;</code></font>
    * Right-click > Run As > Run Configurations...
    * Switch to the Arguments tab
    * Under Program arguments, enter the path to `messenger.cfg` and `quickfix.cfg`
      * Variables... > `${resource_loc}` can aid in locating these configuration files
  1. Running in debug mode should work the same way
    * Right-click > Debug As > Java Application


---

# Source #
## Packages ##
  * **`com.jramoyo`** - Root package
    * **`fix`** - Generic FIX-related classes
      * **`model`** - Generic FIX model classes
    * **`qfixmessenger`** - QuickFIX Messenger specific classes
      * **`quickfix`** - QuickFIX/J components
        * **`parser`** - QuickFIX specific `FixDictionaryParser`
      * **`ui`** - Swing classes
        * **`editors`** - TreeCellEditors, TableCellEditors, etc.
        * **`layers`** - LayerUIs
        * **`models`** - TreeModels, TableModels, etc.
        * **`panels`** - JPanels
        * **`renderers`** - TreeCellRenderers, TableCellRenderers, etc.

## Directories ##
  * **`src`** - Source
  * **`src-gen`** - Generated source
  * **`src-test`** - Unit test source
  * **`lib`** - Libraries
  * **`package`** - Generated JAR files
  * **`deploy`** - Executables
  * **`scripts`** - Executable scripts
  * **`cfg`** - Sample configuration
  * **`resources`** - Resources
    * **`dictionary`** - QuickFIX/J dictionaries (XML)
    * **`icons`** - Icon files
    * **`xsd`** - XML schema files

## Ant Targets ##
  * **`clean.build`** - Cleans the project and build the source code
  * **`clean.package`** - Cleans the project and packages the JAR file
  * **`clean.deploy`** - Cleans the project and creates a working directory
  * **`clean.release`** - Cleans the project and creates a binary distribution package
  * **`clean.source`** - Cleans the project and creates a source distribution package


---

# Development Standards #
## Code Standards ##
_The included Eclipse project files contains the 'Java Code Style' used throughout the project_

### Convention ###
  * Always CTRL-Shift-F (Source > Format) to ensure that the code follows the convention used throughout the project
  * Always CTRL-Shift-O (Source > Organize Imports) to ensure that imports are neat and granular
  * Do not ignore warnings (they're there for a reason)
  * Always use curly braces `{ }` on IF statements, even single liners

### Comments ###
  * For non-UI classes, always provide a Javadoc for public, package-protected, and protected methods.
    * Unless new behavior is added, Javadoc is not required for overridden methods
  * Use `/* */` for multi-line comments
  * Comment on complex logic, avoid too much comments
  * Do not check-in code that's been commented-out (use version history to retrieve previous code)

### Naming ###
  * Nouns for classes
  * Verbs for methods
  * Use descriptive names
  * Always use camel-case, even for acronyms
    * **`XmlParser`** vs. `XMLParser`
  * For directories (including SVN), use hyphen (`-`) to separate words
    * **`my-directory`** vs. `myDirectory` or `my_directory`

## Process ##
  * Code changes must be assigned a ticket
  * Always work on a branch
  * Delete already merged branch