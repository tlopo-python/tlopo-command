# Small library to run commands from python #

## How to install ##
```sh
pip install tlopo_command
```

## How to use ##

Quick usage: 
```python
from tlopo_command import command as cmd
print(cmd("whoami").run().stdout)
```

Use return code: 
```python
from tlopo_command import command as cmd
r = cmd("whoami").run()
print([r.stdout, r.returncode ])
# ['tlopo\n', 0]
```

Use live output (comand stdout and stder immediately flushed to STDOUT and STDERR)
```python
from tlopo_command import command as cmd
cmd("sh -c 'seq 1 10 | while read i; do echo $i; sleep 1 ; done'", live=True).run()
```

Use must_succeed (Throws exception if returncode is non-zero )
```python
from tlopo_command import command as cmd
cmd("sh -c 'exit 1'", must_succeed=True).run()
```
