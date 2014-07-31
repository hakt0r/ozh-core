ozh-core
========

* ozh lightweight shell extensions
* ozh reboot - core module
* 2008-2014 - anx @ ulzq de (Sebastian Glaser)
* Licensed under GNU GPL v3

ozh is a package manager for various un+x-style shells. It's aim is to sanitize the **environment** and provide tools to install and depend upon **modules**.

Modules always live in a *folder* and follow a simple *$mod/$mod* convention as the entry-point.

Installation
------------

    repo="https://raw.githubusercontent.com/hakt0r/ozh-core/master"
    cd; $(which wget) -Oozcore "$repo/core"; . ./ozcore
    ozh install +repo "$repo" core

Basic Usage
-----------


### Install a module

    oz install [+-repo $repo] [+-lib] [+-only] $mod

* *+repo* will force a repo url and save the $OZH/$mod/repo file

* *+lib * will add the following modules to the $OZH/libs file, unless they exist already.

* *-only* will inhibit sourcing the following modules after install. Hooks will not be executed, hence install scripts will not run.

#### Examples

    oz install +lib shell # will be expanded to shell/shell
    oz install +lib shell/abstracts


### View or edit ozh-stuff

#### Get $OZH/libs
    oz get libs

#### Set $OZH/libs to 'core/core'
    oz set libs 'core/core'

#### Open $EDITOR for ...
    oz edit libs
    oz edit shell/motd

License
-------

ozh is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2, or (at your option)
any later version.

ozh is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this software; see the file COPYING.  If not, write to
the Free Software Foundation, Inc., 59 Temple Place, Suite 330,
Boston, MA 02111-1307 USA
