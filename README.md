MQTTLibrary for Robot Framework
===============================

[![PyPI version](https://badge.fury.io/py/robotframework-mqtt5library.svg)](https://badge.fury.io/py/robotframework-mqtt5library)

MQTTLibrary is a [Robot Framework](http://robotframework.org) library
that provides keywords for testing on MQTT brokers.
[MQTT](http://mqtt.org/) is a lightweight protocol for
machine-to-machine communication, typically used for IoT messaging. This
library uses the [paho](https://eclipse.org/paho/) client library
published by eclipse project.

Installation
------------

MQTTLibrary can be installed using [pip](http://pip-installer.org):

    pip install robotframework-mqtt5library

Usage
-----

Import the library:

``` {.robotframework}
*** Settings ***
Library          MQTTLibrary
```

Connect to the broker, publish and disconnect:

``` {.robotframework}
*** Test Cases ***
Publish
    Connect    ${brokerhost}    ${brokerport}    ca_cert=${ca_cert}    certfile=${certfile}    keyfile=${keyfile}
    Publish     topic=test/mqtt_test    message=test message
    [Teardown]  Disconnect
```

Connect to the broker, subscribe and validate that a message is
received:

``` {.robotframework}
*** Test Cases ***
Subscribe and Validate
    Connect    ${brokerhost}    ${brokerport}    ca_cert=${ca_cert}    certfile=${certfile}    keyfile=${keyfile}
    Subscribe and Validate  topic=test/mqtt_test    qos=2   payload=test
    [Teardown]              Disconnect
```

Keyword documentation is available at:
<http://kemilsoderberg.github.io/robotframework-mqtt5library>.

For general information about using test libraries with Robot Framework,
see [Robot Framework User
Guide](http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#using-test-libraries).

Contributing
------------

The keywords in this library are based on some of the methods available
in eclipse paho client library. If you\'d like to add keywords, see
[instructions]() on creating/updating libraries for Robot Framework.

License
-------

MQTT5Library is open source software provided under the [Apache License
2.0](http://apache.org/licenses/LICENSE-2.0).
