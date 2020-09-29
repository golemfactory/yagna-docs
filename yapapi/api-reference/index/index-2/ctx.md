# yapapi.runner.ctx

## Variables

```text
TYPE_CHECKING
```

## Classes

### CommandContainer

```text
class CommandContainer(

)
```

#### Methods

#### commands

```text
def commands(
    self
)
```

### Work

```text
class Work(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.runner.ctx.\_InitStep
* yapapi.runner.ctx.\_SendWork
* yapapi.runner.ctx.\_Run
* yapapi.runner.ctx.\_RecvFile
* yapapi.runner.ctx.\_Steps

#### Methods

#### post

```text
def post(
    self
)
```

#### prepare

```text
def prepare(
    self
)
```

#### register

```text
def register(
    self,
    commands: yapapi.runner.ctx.CommandContainer
)
```

Register a virtual subclass of an ABC.

Returns the subclass, to allow usage as a class decorator.

### WorkContext

```text
class WorkContext(
    ctx_id: str,
    storage: yapapi.storage.StorageProvider,
    emitter: Union[yapapi.runner.events.EventEmitter[yapapi.runner.events.StorageEvent], NoneType] = None
)
```

An object used to schedule commands to be sent to provider.

#### Methods

#### begin

```text
def begin(
    self
)
```

#### commit

```text
def commit(
    self,
    task: 'Task'
) -> Tuple[ForwardRef('Task'), yapapi.runner.ctx.Work]
```

End task-related command list definition.

:param task: task related to the list of commands :return: a tuple of Task and Work objects \(the latter contains sequence commands added before calling this method\)

#### download\_file

```text
def download_file(
    self,
    src_path: str,
    dst_path: str
)
```

Schedule downloading remote file from the provider.

:param src\_path: remote \(provider\) path :param dst\_path: local \(requestor\) path :return: None

#### log

```text
def log(
    self,
    *args
)
```

#### run

```text
def run(
    self,
    cmd: str,
    *args: Iterable[str],
    env: Union[Dict[str, str], NoneType] = None
)
```

Schedule running a command.

:param cmd: command to run on the provider, e.g. /my/dir/run.sh :param args: command arguments, e.g. "input1.txt", "output1.txt" :param env: optional dictionary with environmental variables :return: None

#### send\_file

```text
def send_file(
    self,
    src_path: str,
    dst_path: str
)
```

Schedule sending file to the provider.

:param src\_path: local \(requestor\) path :param dst\_path: remote \(provider\) path :return: None

#### send\_json

```text
def send_json(
    self,
    json_path: str,
    data: dict
)
```

Schedule sending JSON data to the provider.

:param json\_path: remote \(provider\) path :param data: dictionary representing JSON data :return: None

