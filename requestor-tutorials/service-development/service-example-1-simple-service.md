---
description: A proof-of-concept service running within a VM-based runtime.
---

# Service Example 1: Simple service

The idea behind this proof-of-concept, toy-like service is to demonstrate the basic features of the high-level API's Service model running on a regular VM runtime. In other words, utilizing only the existing features of both yagna and the API itself without relying on any additional resources \(like custom runtime/ExeUnit implementation\).

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* VM runtime
* Service execution
  * Interactive command results processing
{% endhint %}

{% hint style="info" %}
The code and components of this POC are included as an example within yapapi: [https://github.com/golemfactory/yapapi/tree/master/examples/simple-service-poc](https://github.com/golemfactory/yapapi/tree/master/examples/simple-service-poc)
{% endhint %}

## The service

The service itself is rather simplistic and designed to reflect a mechanism that periodically polls some external data source and accumulates those observations in a database that can then be queried by the agent which has commissioned it. 

If this was a real-life example, the data could come from some sensor connected to the provider's machine or be effect of the service e.g. polling some external API or web service. Here in our POC, it's just a background process that produces a stream of random numbers with a certain normal distribution.

### Components of our POC service

All components of the service itself - that is - the part that's actually running on a provider node, are included in a VM image and contained within the `simple_service` directory of the example. For the sake of simplicity, all the code is in Python and to limit the size of the VM image the providers need to download, we're relying on an official Python 3.8 slim image plus two additional Python libraries: `numpy` and `matplotlib`.

### Service back-end

The back-end's code resides in `simple_service/simple_service.py` file in the example's directory. It's a simple script with a command-line interface which accepts one of five commands. The usage is as follows:

```bash
usage: simple_service.py [-h]
                         (--add ADD | --init | --plot {time,dist} | --dump | --stats)

simple service

optional arguments:
  -h, --help          show this help message and exit
  --add ADD
  --init
  --plot {time,dist}
  --dump
  --stats
```

Where:

* `--init` is only ever executed once and creates an extremely simple sqlite database \(one table with just two columns, the value and the timestamp of an observation\) to hold observed values in,
* `--add` adds a single value to the stored list of observations,
* `--stats` provides a JSON structure containing a few metrics that reflect the characteristics of the distribution of the accumulated values \(like the mean, deviation and the number of observations so far\),
* `--plot` produces a graphical plot of accumulated observations \(either as a time-series or as a distribution plot\),
* and finally, `--dump` dumps the JSON-serialized contents of the whole database.

Example output of `--stats`:

```javascript
{"min": 8.127806186682104, "max": 22.792308388964692, "median": 13.850778661989605, "mean": 14.480742088585053, "variance": 12.239089690455327, "std dev": 3.4984410371557395, "size": 35}
```

Example output of `--plot`:

![](../../.gitbook/assets/rulkfjiudp.png)

### Source of data

As mentioned, if this was a real-life example, the data could perhaps come from some external sensor, API, website or some other source that we'd like our service to monitor. In our case, the "daemon" is just a simple loop that simulates observations of such a source by generating random values once a second. 

All generated values are then appended to the database by calling the back-end with the `--add` parameter.

The daemon's code is contained in `simple_service/simulate_observations.py`:

```python
import ...

MU = 14
SIGMA = 3

SERVICE_PATH = Path(__file__).absolute().parent / "simple_service.py"


while True:
    v = random.normalvariate(MU, SIGMA)
    os.system(f"{SERVICE_PATH} --add {v}")
    time.sleep(1)
```

### Control script

The final piece of code is the daemon's control script `simple_service/simulate_observations_ctl.py` , the role of which is to enable starting and stopping the daemon. It's again a CLI tool that accepts just one of the two parameters: `--start` and `--stop` which, quite obviously, respectively start and stop the background process which generates the simulated observations.

### Dockerfile

Finally, we put all of the above components together using the following Dockerfile \(`simple_service/simple_service.Dockerfile`\), built on top of Python 3.8's slim image.

```text
FROM python:3.8-slim
VOLUME /golem/in /golem/out
COPY simple_service.py /golem/run/simple_service.py
COPY simulate_observations.py /golem/run/simulate_observations.py
COPY simulate_observations_ctl.py /golem/run/simulate_observations_ctl.py
RUN pip install numpy matplotlib
RUN chmod +x /golem/run/*
RUN /golem/run/simple_service.py --init
ENTRYPOINT ["sh"]

```

What it does is:

* declare the appropriate input/output directories through which files can be exchanged between the VM and the outside world,
* copy all the Python scripts to the appropriate location within the image and make all of them executable,
* install the two additional requirements of our service: `numpy` and `matplotlib`,
* initalizes the service's sqlite database so that it doesn't have to be done in runtime,

{% hint style="warning" %}
It's important to note that the `ENTRYPOINT` statement, though included, is there just for convenience when testing the image in Docker itself. That entrypoint is ignored by Golem's VM runtime and all commands need to be refered to by their absolute paths \(`/golem/run...`\)
{% endhint %}

## Building the image

The requestor agent script included in the example already contains the hash of the image that has been built by us and uploaded to Golem's VM image repository. 

When building your own application though, you'd need to create and upload that image yourself. For full information on how to do that, please refer to our tutorial on [converting a Docker image to Golem's format](../convert-a-docker-image-into-a-golem-image.md).

If you'd like to play around with modifying the included image yourself, please remember to update the service definition's `get_payload` hook to point to your just-uploaded image:

```python
    async def get_payload():
        return await vm.repo(
        image_hash="your-image-hash-here",
        ...
    )
```





  




TODO: mention the current limitation of the VM runtime \(no network support\)

