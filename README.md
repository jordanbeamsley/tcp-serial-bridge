# SIO Bridge
This repo contains the c++ source files for the serial-tcp bridge intended to run with ACP02 and ped04-ipgw-02.

This project solves the problem of ACP02 and ped04-ipgw-02 both requiring access to the same serial port when running on the Reach Technology touchscreens.

This is achieved by acting as a publisher server, to which subscriber applications can "subscribe" to through a telnet port.

Once an application is subscribed it will receive anything that arrives on the serial port, and can write anything to the serial port.

The gateway is capable of scaling to accomodate a large number of TCP connections, should more applications need to access the serial port.

## Requirements
Linux support of epoll(7)

## Building
```
cd $SOURCEDIR
mkdir build
cd build
cmake ..
make
```

## Defaults
Default values defined as constants in source code.

| Parameter   | Default        | Description                |
| :--------   | :------------- | :------------------------- |
| `CONN_HOST` | `localhost`    | Network host address       |
| `CONN_PORT` | `3333`         | Network port               |
| `CONN_TYPE` | `tcp`          | Network type               |
| `SER_PORT`  | `/dev/ttymxc3` | Serial port                |
| `SER_BAUD`  | `9600`         | Serial baud rate           |

*Todo: make default values user definable from CLI and/or config file*  
