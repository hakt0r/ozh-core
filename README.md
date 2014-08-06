ozh-core
========
**ozh *lightweight shell extensions***

* ozh reboot - core module
* 2008-2014 - anx @ ulzq de (Sebastian Glaser)
* Licensed under GNU GPL v3

ozh is a package manager for various un+x-style shells. It's aim is to sanitize the **environment** and provide tools to install and depend upon **modules**.

Modules always live in a *folder* and follow a simple *$mod/$mod* convention as the entry-point.

Installation
------------

    ( tmp=$(mktemp); repo="https://raw.githubusercontent.com/hakt0r/ozh-core/master";
      cd; curl "$repo/core" > "$tmp"; . "$tmp" libs;
      oz printenv; oz install "$repo/core"; rm "$tmp"; )

Then source the core for testing:

    . ~/.config/ozh/core/core libs

If this **works** you should be able to install new modules like this:

    oz install https://raw.githubusercontent.com/hakt0r/ozh-shell/master/shell

You can now safely add ozh to your shell profile:

    echo ". ~/.config/ozh/core/core libs" >> $HOME/.bashrc 
    echo ". ~/.config/ozh/core/core libs" >> $HOME/.zhrc 

Basic Usage
-----------


### Install a module

    oz install [FLAGS] $mod [...]

You can install multiple modules at a time, flags can be placed anywhere in the module list and take effect immediately. Modules can also be a URL in which case the corresponding entry will be set in $OZH/mod/repo.

#### Flags

  * **+lib** will add the following modules to the $OZH/libs file, unless they exist already.
  * **-only** will inhibit sourcing the following modules after install. Hooks will not be executed, hence install scripts will not run.
  * **+prefix** *$prefix* will add a prefix to the following modules as in: $prefix/$mod

#### Examples

    oz install +lib shell                 # will be expanded to shell/shell
    oz install +lib shell/abstracts       # update a module asset
    oz install http://url.to/repo/mod/mod # install mod from the webs

### View or edit ozh-stuff

    oz get libs                           # get $OZH/libs
    oz set libs 'core/core'               # set $OZH/libs to 'core/core'
    oz edit libs                          # open $EDITOR for ...
    oz edit shell/repo


### Hooks

    oz hook run prompt
    oz hook set prompt aa_date date
    oz hook get prompt aa_date
    oz hook edit prompt aa_date
    oz hook del prompt aa_date

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
