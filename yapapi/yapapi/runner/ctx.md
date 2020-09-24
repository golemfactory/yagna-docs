Module yapapi.runner.ctx
========================

Variables
---------

```python3
TYPE_CHECKING
```

Classes
-------

### CommandContainer

```python3
class CommandContainer(
    
)
```

#### Methods

    
#### commands

```python3
def commands(
    self
)
```

### Work

```python3
class Work(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.runner.ctx._InitStep
* yapapi.runner.ctx._SendWork
* yapapi.runner.ctx._Run
* yapapi.runner.ctx._RecvFile
* yapapi.runner.ctx._Steps

#### Methods

    
#### post

```python3
def post(
    self
)
```

    
#### prepare

```python3
def prepare(
    self
)
```

    
#### register

```python3
def register(
    self,
    commands: yapapi.runner.ctx.CommandContainer
)
```
Register a virtual subclass of an ABC.

Returns the subclass, to allow usage as a class decorator.

### WorkContext

```python3
class WorkContext(
    ctx_id: str,
    storage: yapapi.storage.StorageProvider,
    emitter: Union[yapapi.runner.events.EventEmitter[yapapi.runner.events.StorageEvent], NoneType] = None
)
```

An object used to schedule commands to be sent to provider.
    

#### Methods

    
#### begin

```python3
def begin(
    self
)
```

    
#### commit

```python3
def commit(
    self,
    task: 'Task'
) -> Tuple[ForwardRef('Task'), yapapi.runner.ctx.Work]
```
End task-related command list definition.

:param task: task related to the list of commands
:return: a tuple of Task and Work objects (the latter contains
         sequence commands added before calling this method)

    
#### download_file

```python3
def download_file(
    self,
    src_path: str,
    dst_path: str
)
```
Schedule downloading remote file from the provider.

:param src_path: remote (provider) path
:param dst_path: local (requestor) path
:return: None

    
#### log

```python3
def log(
    self,
    *args
)
```

    
#### run

```python3
def run(
    self,
    cmd: str,
    *args: Iterable[str],
    env: Union[Dict[str, str], NoneType] = None
)
```
Schedule running a command.

:param cmd: command to run on the provider, e.g. /my/dir/run.sh
:param args: command arguments, e.g. "input1.txt", "output1.txt"
:param env: optional dictionary with environmental variables
:return: None

    
#### send_file

```python3
def send_file(
    self,
    src_path: str,
    dst_path: str
)
```
Schedule sending file to the provider.

:param src_path: local (requestor) path
:param dst_path: remote (provider) path
:return: None

    
#### send_json

```python3
def send_json(
    self,
    json_path: str,
    data: dict
)
```
Schedule sending JSON data to the provider.

:param json_path: remote (provider) path
:param data: dictionary representing JSON data
:return: None