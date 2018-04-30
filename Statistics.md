# Overview

The "stats" RPC command can be used by external processes to query statistics, such as traffic counters. This is useful for diagnostics, monitoring and display in admin consoles. 

Statistics are optionally logged to separate text files.

For implementations details, please see [Statistics API](https://github.com/cryptocode/raiblocks/wiki/Statistics-API)

## Configuration

All configuration nodes and values are optional, with the default values shown in comments below:

```
"node": {
    ...
    "statistics": {

        // Sampling configuration (optional)
        // Only activate if you need sampling information, as there's some overhead associated with this feature.
        "sampling": {
            "enabled": "true",                // If sampling is enabled. Default false.
            "capacity": "5",                  // How many samples to keep. Must be set if sampling is enabled.
            "interval": "1000"                // Sample interval in milliseconds. Must be set if sampling is enabled.
        },

        // File logging (optional)
        "log": {                              
            "interval_counters": "5000",      // How often to write counters to file in milliseconds. Default 0 (off)
            "interval_samples": "5000",       // How often to write samples to file, milliseconds. Default 0 (off)
            "rotation_count": "5",            // Rotate file after writing statistics this many times. Default 100.
            "headers": "true",                // Write header containing log
            "filename_counters": "counters.stat",
            "filename_samples": "samples.stat"
        }
    }
}
```

## RPC

### Counters query:

```
{
    "action": "stats",
    "type": "counters"
}
```

### Counters response

```
{
    "type": "counters",
    "created": "2018.03.29 01:46:36",
    "entries": [
        {
            "time": "01:46:36",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "3122792"
        },
        {
            "time": "01:46:36",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "203184"
        },
        {
            "time": "01:46:36",
            "type": "message",
            "detail": "all",
            "dir": "in",
            "value": "12494"
        },
        {
            "time": "01:46:36",
            "type": "message",
            "detail": "all",
            "dir": "out",
            "value": "1380"
        },
        {
            "time": "01:46:36",
            "type": "message",
            "detail": "keepalive",
            "dir": "in",
            "value": "172"
        },
        {
            "time": "01:46:36",
            "type": "message",
            "detail": "keepalive",
            "dir": "out",
            "value": "1084"
        },
        {
            "time": "01:46:36",
            "type": "message",
            "detail": "publish",
            "dir": "in",
            "value": "406"
        },
        {
            "time": "01:46:33",
            "type": "message",
            "detail": "confirm_req",
            "dir": "in",
            "value": "165"
        },
        {
            "time": "01:46:33",
            "type": "message",
            "detail": "confirm_req",
            "dir": "out",
            "value": "296"
        },
        {
            "time": "01:46:36",
            "type": "message",
            "detail": "confirm_ack",
            "dir": "in",
            "value": "11751"
        },
        {
            "time": "01:46:36",
            "type": "bootstrap",
            "detail": "all",
            "dir": "out",
            "value": "7965"
        },
        {
            "time": "01:46:36",
            "type": "bootstrap",
            "detail": "initiate",
            "dir": "out",
            "value": "7965"
        }
    ]
}
```

### Samples query:

```
{
    "action": "stats",
    "type": "samples"
}
```
### Samples response

```
{
    "type": "samples",
    "created": "2018.03.29 01:47:08",
    "entries": [
        {
            "time": "01:47:04",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "59480"
        },
        {
            "time": "01:47:05",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "44496"
        },
        {
            "time": "01:47:06",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "44136"
        },
        {
            "time": "01:47:07",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "18784"
        },
        {
            "time": "01:47:08",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "22680"
        },
        {
            "time": "01:47:03",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "4128"
        },
        {
            "time": "01:47:04",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "2136"
        },
        {
            "time": "01:47:05",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "1368"
        },
        {
            "time": "01:47:06",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "3504"
        },
        {
            "time": "01:47:08",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "1368"
        },
        {
            "time": "01:47:04",
            "type": "message",
            "detail": "all",
            "dir": "in",
            "value": "235"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "all",
            "dir": "in",
            "value": "176"
        },
        {
            "time": "01:47:06",
            "type": "message",
            "detail": "all",
            "dir": "in",
            "value": "182"
        },
        {
            "time": "01:47:07",
            "type": "message",
            "detail": "all",
            "dir": "in",
            "value": "78"
        },
        {
            "time": "01:47:08",
            "type": "message",
            "detail": "all",
            "dir": "in",
            "value": "92"
        },
        {
            "time": "01:47:03",
            "type": "message",
            "detail": "all",
            "dir": "out",
            "value": "31"
        },
        {
            "time": "01:47:04",
            "type": "message",
            "detail": "all",
            "dir": "out",
            "value": "17"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "all",
            "dir": "out",
            "value": "10"
        },
        {
            "time": "01:47:06",
            "type": "message",
            "detail": "all",
            "dir": "out",
            "value": "29"
        },
        {
            "time": "01:47:08",
            "type": "message",
            "detail": "all",
            "dir": "out",
            "value": "9"
        },
        {
            "time": "01:47:03",
            "type": "message",
            "detail": "keepalive",
            "dir": "in",
            "value": "10"
        },
        {
            "time": "01:47:04",
            "type": "message",
            "detail": "keepalive",
            "dir": "in",
            "value": "8"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "keepalive",
            "dir": "in",
            "value": "7"
        },
        {
            "time": "01:47:06",
            "type": "message",
            "detail": "keepalive",
            "dir": "in",
            "value": "12"
        },
        {
            "time": "01:47:08",
            "type": "message",
            "detail": "keepalive",
            "dir": "in",
            "value": "2"
        },
        {
            "time": "01:47:03",
            "type": "message",
            "detail": "keepalive",
            "dir": "out",
            "value": "28"
        },
        {
            "time": "01:47:04",
            "type": "message",
            "detail": "keepalive",
            "dir": "out",
            "value": "16"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "keepalive",
            "dir": "out",
            "value": "10"
        },
        {
            "time": "01:47:06",
            "type": "message",
            "detail": "keepalive",
            "dir": "out",
            "value": "28"
        },
        {
            "time": "01:47:08",
            "type": "message",
            "detail": "keepalive",
            "dir": "out",
            "value": "9"
        },
        {
            "time": "01:47:02",
            "type": "message",
            "detail": "publish",
            "dir": "in",
            "value": "11"
        },
        {
            "time": "01:47:04",
            "type": "message",
            "detail": "publish",
            "dir": "in",
            "value": "15"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "publish",
            "dir": "in",
            "value": "7"
        },
        {
            "time": "01:47:06",
            "type": "message",
            "detail": "publish",
            "dir": "in",
            "value": "3"
        },
        {
            "time": "01:47:08",
            "type": "message",
            "detail": "publish",
            "dir": "in",
            "value": "11"
        },
        {
            "time": "01:46:56",
            "type": "message",
            "detail": "confirm_req",
            "dir": "in",
            "value": "44"
        },
        {
            "time": "01:47:00",
            "type": "message",
            "detail": "confirm_req",
            "dir": "in",
            "value": "5"
        },
        {
            "time": "01:47:01",
            "type": "message",
            "detail": "confirm_req",
            "dir": "in",
            "value": "3"
        },
        {
            "time": "01:47:03",
            "type": "message",
            "detail": "confirm_req",
            "dir": "in",
            "value": "3"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "confirm_req",
            "dir": "in",
            "value": "1"
        },
        {
            "time": "01:46:55",
            "type": "message",
            "detail": "confirm_req",
            "dir": "out",
            "value": "4"
        },
        {
            "time": "01:47:00",
            "type": "message",
            "detail": "confirm_req",
            "dir": "out",
            "value": "12"
        },
        {
            "time": "01:47:01",
            "type": "message",
            "detail": "confirm_req",
            "dir": "out",
            "value": "3"
        },
        {
            "time": "01:47:03",
            "type": "message",
            "detail": "confirm_req",
            "dir": "out",
            "value": "3"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "confirm_req",
            "dir": "out",
            "value": "1"
        },
        {
            "time": "01:47:04",
            "type": "message",
            "detail": "confirm_ack",
            "dir": "in",
            "value": "202"
        },
        {
            "time": "01:47:05",
            "type": "message",
            "detail": "confirm_ack",
            "dir": "in",
            "value": "164"
        },
        {
            "time": "01:47:06",
            "type": "message",
            "detail": "confirm_ack",
            "dir": "in",
            "value": "163"
        },
        {
            "time": "01:47:07",
            "type": "message",
            "detail": "confirm_ack",
            "dir": "in",
            "value": "65"
        },
        {
            "time": "01:47:08",
            "type": "message",
            "detail": "confirm_ack",
            "dir": "in",
            "value": "86"
        },
        {
            "time": "01:47:04",
            "type": "bootstrap",
            "detail": "all",
            "dir": "out",
            "value": "78"
        },
        {
            "time": "01:47:05",
            "type": "bootstrap",
            "detail": "all",
            "dir": "out",
            "value": "72"
        },
        {
            "time": "01:47:06",
            "type": "bootstrap",
            "detail": "all",
            "dir": "out",
            "value": "72"
        },
        {
            "time": "01:47:07",
            "type": "bootstrap",
            "detail": "all",
            "dir": "out",
            "value": "14"
        },
        {
            "time": "01:47:08",
            "type": "bootstrap",
            "detail": "all",
            "dir": "out",
            "value": "138"
        },
        {
            "time": "01:47:04",
            "type": "bootstrap",
            "detail": "initiate",
            "dir": "out",
            "value": "78"
        },
        {
            "time": "01:47:05",
            "type": "bootstrap",
            "detail": "initiate",
            "dir": "out",
            "value": "72"
        },
        {
            "time": "01:47:06",
            "type": "bootstrap",
            "detail": "initiate",
            "dir": "out",
            "value": "72"
        },
        {
            "time": "01:47:07",
            "type": "bootstrap",
            "detail": "initiate",
            "dir": "out",
            "value": "14"
        },
        {
            "time": "01:47:08",
            "type": "bootstrap",
            "detail": "initiate",
            "dir": "out",
            "value": "138"
        }
    ]
}
```


## Log file example

`counters.stat`

As specified in the example config, sampling interval is 1 second, stats are logged every 5 seconds, and the file rotates after 5 log cycles.

```
counters,2018.03.29 01:45:36
01:44:56,bootstrap,all,out,1
01:45:36,bootstrap,initiate,out,2
counters,2018.03.29 01:45:41
01:45:41,traffic,all,in,456344
01:45:41,traffic,all,out,189520
01:45:41,message,all,in,1925
01:45:41,message,all,out,1289
01:45:38,message,keepalive,in,165
01:45:41,message,keepalive,out,1027
01:45:41,message,publish,in,34
01:45:38,message,confirm_req,in,164
01:45:41,message,confirm_req,out,262
01:45:41,message,confirm_ack,in,1562
01:45:36,bootstrap,all,out,2
01:45:41,bootstrap,initiate,out,3
```

`samples.stat`

As specified in the example config, logging is done every 5 seconds and the sampling capacity is 5 (how many samplings are kept)

```
samples,2018.03.29 01:45:36
01:45:36,bootstrap,initiate,out,2
samples,2018.03.29 01:45:41
01:45:37,traffic,all,in,322608
01:45:38,traffic,all,in,37064
01:45:39,traffic,all,in,38752
01:45:40,traffic,all,in,25632
01:45:38,traffic,all,out,185072
01:45:39,traffic,all,out,3072
01:45:41,traffic,all,out,920
01:45:37,message,all,in,1387
01:45:38,message,all,in,126
01:45:39,message,all,in,179
01:45:40,message,all,in,101
01:45:37,message,all,out,1254
01:45:38,message,all,out,10
01:45:39,message,all,out,16
01:45:41,message,all,out,6
01:45:38,message,keepalive,in,165
01:45:38,message,keepalive,out,1011
01:45:39,message,keepalive,out,12
01:45:41,message,keepalive,out,3
01:45:37,message,publish,in,19
01:45:38,message,publish,in,8
01:45:40,message,publish,in,3
01:45:41,message,publish,in,4
01:45:38,message,confirm_req,in,164
01:45:37,message,confirm_req,out,249
01:45:38,message,confirm_req,out,3
01:45:39,message,confirm_req,out,6
01:45:41,message,confirm_req,out,3
01:45:37,message,confirm_ack,in,1046
01:45:38,message,confirm_ack,in,141
01:45:39,message,confirm_ack,in,150
01:45:40,message,confirm_ack,in,100
01:45:36,bootstrap,all,out,2
01:45:36,bootstrap,initiate,out,2
01:45:41,bootstrap,initiate,out,1
```

