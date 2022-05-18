
# Controlcenter

This is a simple script to preform basic docker commands i.e. `enable`, `disable`, `update`, `start`, `stop`, `restart`, and `pull`.

It also allows users to `create`, `edit`, and `delete` existing containers; as well as view current and past `logs`.




## Features

- Console script: `controlcenter`
- UI script (dialog): `controlcenter-ui`
- Custom `pull`, `restart`, `start`, `stop`, and/or `update` scripts defined per-container



## Installation

Everything needed should come preinstalled with linux.

However, if you would like to run the command from anywhere follow this guide.

```bash
ln -s /path/to/install/controlcenter /usr/local/bin/
ln -s /path/to/install/controlcenter-ui /usr/local/bin/
```
I would only recomend symlinking these two scripts. The others can be run standalone, but should only be done in the installation folder.

In order for the script to run as a normal user, you must be part of the `docker` group.
## Screenshots



## Documentation


Each script by default uses the `pull`, `restart`, `start`, `stop`, and `update` scripts contained in the `containers>scripts` folder.

The default scripts can be overridden. The `TEMPLATE` container contains a `scripts` folder; inside are example scripts. These scripts
can be renamed from `"script_name"_example` to `"script_name"`. The `controlcenter` will automatically use the overridden script.

### Controlcenter
Console script

| Parameter | Description                                                             |
| :-------- | :---------------------------------------------------------------------- |
| `-v`      | **Optional**. If set, the output will not clear upon command completion |

#### Examples
```
controlcenter -v
```
Runs in verbose mode
```
controlcenter
```
Runs in non-verbose mode

### Disable
Disables the targeted container

| Parameter | Description                                                                    |
| :-------- | :----------------------------------------------------------------------------- |
| `-h`      | **Optional**. Displays the help text                                           |
| `-q`      | **Optional**. If set, will not display the info banner                         |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose |
| `-c`      | **Required**. The container to target                                          |

#### Examples
```
disable -qac nextcloud
```
Disables the container `nextcloud` without ANSI control characters and in quite mode


### Enable
Enables the targeted container

| Parameter | Description                                                                    |
| :-------- | :----------------------------------------------------------------------------- |
| `-h`      | **Optional**. Displays the help text                                           |
| `-n`      | **Optional**. If set, will immediently start the container                     |
| `-f`      | **Optional**. If set, will force enable the container (disable, then enable)   |
| `-q`      | **Optional**. If set, will not display the info banner                         |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose |
| `-c`      | **Required**. The container to target                                          |

#### Examples
```
enable -anfc nextcloud
```
Enables the container `nextcloud` without ANSI control characters, enables immediently, and forces it enabled

```
enable -qac nextcloud
```
Enables the container `nextcloud` without ANSI control characters and in quite mode

### Pull
Pulls the lates image for the target container(s)

| Parameter | Description                                                                           |
| :-------- | :------------------------------------------------------------------------------------ |
| `-h`      | **Optional**. Displays the help text                                                  |
| `-q`      | **Optional**. If set, will not display the info banner                                |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose        |
| `-c`      | **Optional**. The container to target. If not set, will target all enabled containers |

#### Examples
```
pull -c nextcloud
```
Pulls the container `nextcloud`

```
pull
```
Pulls all enabled containers

### Restart
Restarts the target container(s)

| Parameter | Description                                                                           |
| :-------- | :------------------------------------------------------------------------------------ |
| `-h`      | **Optional**. Displays the help text                                                  |
| `-q`      | **Optional**. If set, will not display the info banner                                |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose        |
| `-c`      | **Optional**. The container to target. If not set, will target all enabled containers |

#### Examples
```
restart -c nextcloud
```
Restarts the container `nextcloud`

```
restart
```
Restarts all enabled containers

### Start
Starts the target container(s)

| Parameter | Description                                                                           |
| :-------- | :------------------------------------------------------------------------------------ |
| `-h`      | **Optional**. Displays the help text                                                  |
| `-q`      | **Optional**. If set, will not display the info banner                                |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose        |
| `-c`      | **Optional**. The container to target. If not set, will target all enabled containers |

#### Examples
```
start -c nextcloud
```
Starts the container `nextcloud`

```
start
```
Starts all enabled containers

### Stop
Stops the target container(s)

| Parameter | Description                                                                           |
| :-------- | :------------------------------------------------------------------------------------ |
| `-h`      | **Optional**. Displays the help text                                                  |
| `-q`      | **Optional**. If set, will not display the info banner                                |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose        |
| `-c`      | **Optional**. The container to target. If not set, will target all enabled containers |

#### Examples
```
stop -c nextcloud
```
Stops the container `nextcloud`

```
stop
```
Stops all enabled containers

### Update
Updates the target container(s)

| Parameter | Description                                                                           |
| :-------- | :------------------------------------------------------------------------------------ |
| `-h`      | **Optional**. Displays the help text                                                  |
| `-q`      | **Optional**. If set, will not display the info banner                                |
| `-a`      | **Optional**. If set, will not use ANSI control characters from docker-compose        |
| `-c`      | **Optional**. The container to target. If not set, will target all enabled containers |

#### Examples
```
update -c nextcloud
```
Updates the container `nextcloud`

```
update
```
Updates all enabled containers




## TODO

- [X]  Add default scripts with the ability to override at a per-container level
- [X]  Add a way to view logs for failures/details on run for `controlcenter-ui`
- [X]  Add a way to add new containers from the UI
- [X]  Add a way to edit the `docker-compose.yml` and `.env` files from the UI
- [X]  Add a way to define custom config file locations
- [X]  Seperate functions into seperate scripts, and move scripts to `bin` folder
