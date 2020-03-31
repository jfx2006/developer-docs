---
description: >-
  A high-level look at the project's architecture and a guide to where to find
  things.
---

# Codebase Overview

## Overview of Comm Central

The following directories are included in the comm-central repository:

**build**  
Miscellaneous files used by the build process.

**calendar**  
Source code of the Lightning extension and Google Calendar Provider extension.

**chat**  
Files for the chat component of Thunderbird. There is also related code in `mail/components/im`.

**common**  
An assortment of code we've uplifted from mozilla-central as it was removed from there.

**db**  
The mork database.

**editor**  
UI for the Compose window \(Thunderbird/SeaMonkey\) and the Composer part of SeaMonkey.

**ldap**  
The LDAP C SDK. Used for communicating with LDAP servers.

**mail**  
Thunderbird specific source code. It's no coincidence that this folder is laid out a lot like the `browser` and `toolkit` directories on mozilla-central. Many of the subdirectories follow the same pattern:

* **content** User interface files which become `chrome://messenger/content/…`.
* **modules** Javascript modules which become `resource:///modules/…`.
* **test** Mochitest and/or XPCShell tests.

The subdirectories are:

* **app** Configuration and packaging instructions. Contains `all-thunderbird.js`, the default preferences.
* **base** The main mail window and several miscellaneous dialogs. Also, things which are common to many parts of the program.
* **branding** Icons and imagery.
* **components** Various Thunderbird features, including:
  * **accountcreation** The account setup wizard.
  * **addrbook** The address book user front end. \(Not the address book back end, which is in `mailnews/addrbook`\).
  * **cloudfile** The cloud attachment feature \(a.k.a. FileLink\).
  * **compose** Email composition window.
  * **extensions** WebExtensions schema and implementation.
  * **im** The chat front end.
  * **preferences** The preferences tab.
* **config** Build instructions, including the automation mozconfig files.
* **extensions**
* **installer** Packaging and installation instructions.
* **locales** The user-visible strings, in US English. Files from this directory become `chrome://messenger/locale/…`.
* **test** The MozMill user interface tests and the code to run that test suite.
* **themes** Common and platform-specific styling of Thunderbird user interface. Files from this directory become `chrome://messenger/skin/…`.

**mailnews**  
Source code specific to the Mail and Newsgroups part of Thunderbird and SeaMonkey.

**other-licenses**  
Code that is not under the Mozilla license. See [http://www.mozilla.org/MPL/](http://www.mozilla.org/MPL/) for more info.

**suite**  
SeaMonkey specific source code.

**taskcluster**  
Files needed for Thunderbird's build infrastructure.

**testing**  
Files needed for Thunderbird's test infrastructure.

