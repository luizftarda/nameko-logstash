# Nameko - Logstash Depedency Injector



## Installation

```bash
git clone https://github.com/jdsolucoes/nameko-logstash.git
cd nameko-logstash
python setup.py install
```



## Configuration

Just add a LOGSTASH entry in your name config.yaml file, like this:

```yaml
LOGSTASH:
    HOST: logstash_server.abc.xyz
    PORT: 5959
    LOG_LEVEL: INFO
```



## Usage

just add the LogstashDependency in your service, like this:

```python
from nameko.rpc import rpc
from nameko_logstash import LogstashDependency


class MyService(object):

    name = 'dumb_service'
    log = LogstashDependency()

    @rpc
    def ping(self):
        self.log.info('Ping received.')
        return 'pong'
```



