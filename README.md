# This repository is deprecated

`vsdcli` is now part of [`vspk`](https://pypi.python.org/pypi/vspk/). Install
it with:

```
pip install vspk
```

## Usage

Follow the CLI help menu:

    $ vsd -h

You can define following environments variables:

* `vsd_USERNAME` user name
* `vsd_PASSWORD` user password
* `vsd_API_URL` API URL
* `vsd_ENTERPRISE` Enterprise name

Examples:

```
$ vsd list enterprises --api https://vsd:8443 --username csproot --password csproot --enterprise csp --version 3.2

$ export VSD_PASSWORD=csproot
$ export VSD_USERNAME=csproot
$ export VSD_ENTERPRISE=csp
$ export VSD_API_VERSION=3.2
$ export VSD_API_URL=https://vsd:8443

$ vsd list enterprises
$ vsd list enterprises -f "name == 'My Company'"
$ vsd list enterprises -x ID name   # List name and ID only
$ vsd list enterprises -x ALL       # List all fields
$ vsd list vports --in subnet a3db271b-b4ab-45a2-995e-971bf9e761bb
$ vsd show domain --id 04850601-bebb-4b9b-acac-a31b455595a4

$ vsd count vports --in subnet 67add3a4-5bd5-42a5-8231-b6710dac3546 -x name

$ vsd create zone --in domain dd960a1f-b555-4e6c-9bf5-f88832679b5e -p name='Test Zone' IPType=IPV4 numberOfHostsInSubnets=4 maintenanceMode=DISABLED
$ vsd create enterprise -p name='My Company'

$ vsd update enterprise -i 26f67b33-3601-4cdf-8ed0-fba7116d0200 -p name='Example'
$ vsd update zone -i c4e96631-cfbc-4dcd-a4c3-b2937e5eab13 -p name='Danger Zone'


$ vsd assign users --ids f30061e8-56dc-47cc-ab9e-cf0d30fe1563 e838617f-658d-41a2-af46-bc54da0055fe --to group 74fb343a-093b-4738-bd59-135dc9e1aa78
$ vsd unassign users --ids f30061e8-56dc-47cc-ab9e-cf0d30fe1563 e838617f-658d-41a2-af46-bc54da0055fe --from group 74fb343a-093b-4738-bd59-135dc9e1aa78
$ vsd reassign users --ids d7162530-6960-43bb-a400-db0dbdeea06e --to group 74fb343a-093b-4738-bd59-135dc9e1aa78
$ vsd reassign users --to group 74fb343a-093b-4738-bd59-135dc9e1aa78  # Remove all users assigned to the specified group

$ vsd objects                           # List all objects
$ vsd objects -f nsg                    # List all objects that contains word nsg
$ vsd objects -p enterprise             # List all objects that have an enterprise as parent
$ vsd objects -c domain                 # List all objects that have a domain as child
$ vsd objects -p enterprise -c domain   # List all objects that have an enterprise as parent and a domain as child
```

### Available commands

Here are a list of available commands:
* `list`
* `count`
* `show`
* `create`
* `update`
* `delete`
* `assign` : to add one or multiple assignations to existing ones
* `unassign`: to remove one or multiple assignations to existing ones
* `reassign`: to reset all assignation.
* `objects` will enable you to traverse VSD objects hierarchy


## License

Copyright (c) 2015, Alcatel-Lucent Inc
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of the copyright holder nor the names of its contributors
      may be used to endorse or promote products derived from this software without
      specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
