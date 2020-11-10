---
description: Symptoms and solutions of known issues.
---

# Common issues

### No access to VM

_Description:_ No access to VM

 _Solution:_ `curl -o setup-kvm.sh https://join.golem.network/setup-kvm.sh && chmod +x ./setup-kvm.sh && ./setup-kvm.sh` 

Note: make sure `qemu-vm` is installed first with `apt install qemu-kvm`.

### IO error: No such file or directory

_Os:_ Any

_Description:_  Local service error: Transfer error: IO error: No such file or directory \(os error 2\)

_Solution:_  Something went wrong with the computation, the user could write a log file or doing some checks and then pulling that back instead of their output. Example: [https://discord.com/channels/684703559954333727/756161015493951600/767132601248907307](https://discord.com/channels/684703559954333727/756161015493951600/767132601248907307) Other potential solution: [https://discord.com/channels/684703559954333727/756161015493951600/769671518903992320](https://discord.com/channels/684703559954333727/756161015493951600/769671518903992320)

### Dependency issues

_Os: Ubuntu_

_Description:_ If someone has a minimal install of Ubuntu they can run into dependency issues

_Solution:_ the issue is related to `syslink`_._

### Blender example error on python 3.6/Windows

_Os:_ Windows

_Description:_ running blender example on Windows \(python 3.6\) gives the error message as below:

```text
(yagna-python-tutorial) C:\Users\ederenn\Projects\yapapi\examples\blender>python blender.py --subnet-tag devnet-alpha.2
Adding C:\Users\ederenn\Projects\yapapi\examples to sys.path.
yapapi version: 0.3.0
Using subnet: devnet-alpha.2

Traceback (most recent call last):
  File "blender.py", line 102, in <module>
    asyncio.get_event_loop().run_until_complete(task)
  File "C:\Users\ederenn\AppData\Local\Programs\Python\Python36\lib\asyncio\base_events.py", line 467, in run_until_complete
    return future.result()
  File "blender.py", line 98, in <module>
    asyncio.get_event_loop().run_until_complete(task)
  File "C:\Users\ederenn\AppData\Local\Programs\Python\Python36\lib\asyncio\base_events.py", line 467, in run_until_complete
    return future.result()
  File "blender.py", line 76, in main
    async for task in engine.map(worker, [Task(data=frame) for frame in frames]):
  File "C:\Users\ederenn\.envs\yagna-python-tutorial\lib\site-packages\yapapi\runner\__init__.py", line 362, in map
    storage_manager = await self._stack.enter_async_context(gftp.provider())
  File "C:\Users\ederenn\.envs\yagna-python-tutorial\lib\site-packages\async_exit_stack\_async_exit_stack.py", line 115, in enter_async_context
    result = await _cm_type.__aenter__(cm)
  File "C:\Users\ederenn\.envs\yagna-python-tutorial\lib\site-packages\yapapi\storage\gftp.py", line 211, in __aenter__
    process = await self.__get_process()
  File "C:\Users\ederenn\.envs\yagna-python-tutorial\lib\site-packages\yapapi\storage\gftp.py", line 236, in __get_process
    process = self._process or (await self.__exit_stack.enter_async_context(service(_debug)))
  File "C:\Users\ederenn\.envs\yagna-python-tutorial\lib\site-packages\async_exit_stack\_async_exit_stack.py", line 115, in enter_async_context
    result = await _cm_type.__aenter__(cm)
  File "C:\Users\ederenn\.envs\yagna-python-tutorial\lib\site-packages\yapapi\storage\gftp.py", line 93, in __aenter__
    "gftp server", stdout=asyncio.subprocess.PIPE, stdin=asyncio.subprocess.PIPE, env=env
  File "C:\Users\ederenn\AppData\Local\Programs\Python\Python36\lib\asyncio\subprocess.py", line 210, in create_subprocess_shell
    stderr=stderr, **kwds)
  File "C:\Users\ederenn\AppData\Local\Programs\Python\Python36\lib\asyncio\base_events.py", line 1161, in subprocess_shell
    protocol, cmd, True, stdin, stdout, stderr, bufsize, **kwargs)
  File "C:\Users\ederenn\AppData\Local\Programs\Python\Python36\lib\asyncio\coroutines.py", line 212, in coro
    res = func(*args, **kw)
  File "C:\Users\ederenn\AppData\Local\Programs\Python\Python36\lib\asyncio\base_events.py", line 340, in _make_subprocess_transport
    raise NotImplementedError
NotImplementedError

(yagna-python-tutorial) C:\Users\ederenn\Projects\yapapi\examples\blender>
```

_Solution:_ check-out the latest yapapi/b0.3

### Connectivity issue

_Os: All_

_Description:_ When someone is not receiving tasks at all, has correct subnet configured, and VM valid, the most probable cause is yagna "connectivity" issue

_Solution:_ Kill and restart the process

