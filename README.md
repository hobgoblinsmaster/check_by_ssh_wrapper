check_by_ssh_wrapper
====================

<!-- Piwik Image Tracker-->
<img src="https://stats.hobgoblins-master.info/piwik.php?idSite=2&rec=1" style="border:0" alt="" />
<!-- End Piwik -->

This script provides access to commands declared in nrpe to check_by_ssh.
Please set the nrpeconf variable to the right value.
You must generate a ssh key on the nagios server, copy it in .ssh/authorized_keys
in nagios (or nrpe) user home directory on distant server, then add this at
the begining of the line juste before the key:
```
no-pty,no-port-forwarding,command="/usr/local/bin/check_by_ssh_wrapper $SSH_ORIGINAL_COMMAND"
```

You can then use $USER1$/check_by_ssh -H <distant host> -l nagios -C 'check_cmd [args]'

Freely inspired by nagios_ssh_framework. Can be used when nrpe port can't be accessed
or check_command returns to many text for nrpe and you want to keep facilities of nrpe
config files.

[See my blog](http://hobgoblins-master.info/en/posts/check_by_ssh_wrapper.html)

Changes an Modifications:
2011-10-12 - Landry MINOZA - V 1.0
Created because check_disks returns to many lines for nrpe with one of my servers

Copyright: Telbase Formation Conseil, MUSEE D'ORSAY 2011

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
