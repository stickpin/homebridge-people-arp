***
# homebridge-people-arp
This is a plugin for [homebridge](https://github.com/nfarina/homebridge). 
It monitors who is at home, based on their smartphone being seen on the network recently.
Monitoring done using Ping->ARP sequence to increase accuracy.
People displayed as Contact/Door/Window sensor which allow you to triffer notifications when somebody enters or leaving the home (network).
If you use the EVE.app you can also see the presence history of every person-sensor (powered by fakegato) 

# Installation

1. Install homebridge (if not already installed) using: `npm install -g homebridge`
2. Install this plugin using: `npm install -g --unsafe-perm homebridge-people-arp`
3. Update your configuration file. See below for a sample.

# Configuration

```
"platforms": [
    {
        "platform": "PeopleARP",
        "threshold" : 3,
        "cacheDirectory": "./.node-persist/storage",
        "checkInterval": 10000,
        "people" : [
            {
                "name" : "Pete",
                "target" : "PetesiPhone",
                "macAddress" : "de:ef:38:29:0c:28",
                "threshold" : 3,
                "checkInterval": 10000,
                "ignoreReEnterExitSeconds": 0
            },
            {
                "name" : "Someone Else",
                "target" : "192.168.1.68",
                "macAddress" : "64:2e:fb:8b:41:7b",
                "threshold" : 3,
                "checkInterval": 10000,
                "ignoreReEnterExitSeconds": 0
            }
        ]
    }
]
```

| Parameter                  | Note                                                                                                                                                                                         |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `threshold`                | optional, in minutes, default: 3                                                                                                                                                             |
| `cacheDirectory`           | optional, default: "./.node-persist/storage"                                                                                                                                                 |
| `checkInterval`            | optional, in milliseconds, default: 10000. minimal value: 10000                                                                                                                              |
| `target`                   | may be either a hostname or IP address                                                                                                                                                       |
| `macAddress`               | mac address of the device                                                                                                                                                                    |
| `name`                     | a human-readable name for your sensor                                                                                                                                                        |


# Thanks
Thanks to everyone who's helped contribute code, feedback and support.  In particular:
* [PeteLawrence](https://github.com/PeteLawrence/homebridge-people) - for the original plugin
* [skrollme](https://github.com/skrollme/homebridge-people-x) - for the plugin which this one is forked from
* [simont77](https://github.com/simont77/fakegato-history) - for the fakegato-plugin
