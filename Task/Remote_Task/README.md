# Remote Task
Execute task on remote server by a command execution on a local server.

![aaa](./test.c)

## fabric2 (Python3)
`fabric2` is version 2 of `fabric`, which is a module in Python2.
In Python3, `faric2` is treated as `fabric`.
Combination of this and `~/.ssh/config` settings and `ssh-agent` is better.

### Install
```
$ pip install fabric
```

### Use as a command line
A function decorated as invoke.task in ./fabfile.py can be used as one command.

In this mode, be careful about
- Underbar(_) is not usable as argument names.
- Underbar in function name is replaced with hyphen(-).

#### Example 1
An example task to write string in a file on a remote server.
As \<host name\>, you can use names in ~/.ssh/config.

```
fabfile.py
==========

#!/usr/bin/env python
# -*- coding: utf-8 -*-
from fabric import Connection, Config
from invoke import task
import os
Config.ssh_config_path = os.environ['HOME'] + '/.ssh/config'


@task
def remoteEcho(c, exedir='~/', outfile='test', message='Hello fabric!', hostname='<host name>'):
    with Connection(host=hostname) as c:
        with c.cd('{}'.format(exedir)):
            command = 'echo {} > {}'.format(message, outfile)
            c.run(command)
    return
```

```
$ fab -l # show executable tasks
$ fab remoteEcho  
$ fab remoteEcho --message="hoge a" # with argument
```

#### Example 2
This is a task for any shell command.

```
fabfile.py
==========

#!/usr/bin/env python
# -*- coding: utf-8 -*-
from fabric import Connection, Config
from invoke import task
import os
Config.ssh_config_path = os.environ['HOME'] + '/.ssh/config'


@task
def remoteCommand(c, exedir='~/', command='echo xxx', hostname='<host name>'):
    with Connection(host=hostname) as c:
        with c.cd('{}'.format(exedir)):
            c.run(command)
    return
```

```
$ fab -l # show executable tasks
$ fab remoteCommand --command='ls > test' --exedir=='~/test/'
```

