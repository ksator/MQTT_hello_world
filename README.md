### About MQTT

MQTT (Message Queuing Telemetry Transport) is a pub/sub messaging protocol that works on top of TCP/IP.  
Multiple MQTT clients connect to a central communication point, called an “MQTT Broker“, and subscribe to topics that they are interested in.  
These same clients can also publish messages to the central broker.  
The default TCP Port for MQTT is 1883  
The default TCP Port for MQTT over SSL is 8883  

### About Mosquitto

Mosquitto is an open-source message broker that implements the MQTT protocol 

### Install Mosquitto MQTT Broker 

From ubuntu 16.04, add the Mosquitto PPA repository so that we can get the latest version of Mosquitto:

```
$ sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa

 More info: https://launchpad.net/~mosquitto-dev/+archive/ubuntu/mosquitto-ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmptt5znugn/secring.gpg' created
gpg: keyring `/tmp/tmptt5znugn/pubring.gpg' created
gpg: requesting key 262C4500 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmptt5znugn/trustdb.gpg: trustdb created
gpg: key 262C4500: public key "Launchpad mosquitto" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

Update Ubuntu’s package list:   

```
$ sudo apt-get update
Get:1 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial InRelease [23.8 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:3 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial/main amd64 Packages [2,048 B]
Hit:4 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:5 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial/main i386 Packages [2,052 B]
Hit:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Get:7 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial/main Translation-en [1,296 B]
Hit:8 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Fetched 131 kB in 0s (346 kB/s)
Reading package lists... Done
```

Install the Mosquitto Broker
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
```
```
$ sudo apt-get install mosquitto
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libev4 libuv1 libwebsockets7
The following NEW packages will be installed:
  libev4 libuv1 libwebsockets7 mosquitto
0 upgraded, 4 newly installed, 0 to remove and 66 not upgraded.
Need to get 280 kB of archives.
After this operation, 724 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libuv1 amd64 1.8.0-1 [57.4 kB]
Get:2 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial/main amd64 mosquitto amd64 1.4.15-0mosquitto1~xenial1 [135 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libev4 amd64 1:4.22-1 [26.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libwebsockets7 amd64 1.7.1-1 [61.0 kB]
Fetched 280 kB in 0s (2,785 kB/s)
Selecting previously unselected package libuv1:amd64.
(Reading database ... 60187 files and directories currently installed.)
Preparing to unpack .../libuv1_1.8.0-1_amd64.deb ...
Unpacking libuv1:amd64 (1.8.0-1) ...
Selecting previously unselected package libev4.
Preparing to unpack .../libev4_1%3a4.22-1_amd64.deb ...
Unpacking libev4 (1:4.22-1) ...
Selecting previously unselected package libwebsockets7:amd64.
Preparing to unpack .../libwebsockets7_1.7.1-1_amd64.deb ...
Unpacking libwebsockets7:amd64 (1.7.1-1) ...
Selecting previously unselected package mosquitto.
Preparing to unpack .../mosquitto_1.4.15-0mosquitto1~xenial1_amd64.deb ...
Unpacking mosquitto (1.4.15-0mosquitto1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up libuv1:amd64 (1.8.0-1) ...
Setting up libev4 (1:4.22-1) ...
Setting up libwebsockets7:amd64 (1.7.1-1) ...
Setting up mosquitto (1.4.15-0mosquitto1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
```

### Check the Mosquitto service 

Mosquitto service automatically start after installation. You can check the Mosquitto service using the command ```/etc/init.d/mosquitto status```  

```
$ sudo /etc/init.d/mosquitto status
● mosquitto.service - LSB: mosquitto MQTT v3.1 message broker
   Loaded: loaded (/etc/init.d/mosquitto; bad; vendor preset: enabled)
   Active: active (running) since Thu 2018-04-05 10:47:39 CEST; 1min 37s ago
     Docs: man:systemd-sysv-generator(8)
   CGroup: /system.slice/mosquitto.service
           └─2630 /usr/sbin/mosquitto -c /etc/mosquitto/mosquitto.conf

Apr 05 10:47:39 jedi-2 systemd[1]: Starting LSB: mosquitto MQTT v3.1 message broker...
Apr 05 10:47:39 jedi-2 mosquitto[2621]:  * Starting network daemon: mosquitto
Apr 05 10:47:39 jedi-2 mosquitto[2621]:    ...done.
Apr 05 10:47:39 jedi-2 systemd[1]: Started LSB: mosquitto MQTT v3.1 message broker.
```

To stop the Mosquitto Broker service, use the command ```sudo /etc/init.d/mosquitto stop```  

```
$ sudo /etc/init.d/mosquitto stop
[ ok ] Stopping mosquitto (via systemctl): mosquitto.service.
```
```
$ sudo /etc/init.d/mosquitto status
● mosquitto.service - LSB: mosquitto MQTT v3.1 message broker
   Loaded: loaded (/etc/init.d/mosquitto; bad; vendor preset: enabled)
   Active: inactive (dead) since Thu 2018-04-05 10:53:12 CEST; 4s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2823 ExecStop=/etc/init.d/mosquitto stop (code=exited, status=0/SUCCESS)
    Tasks: 0
   Memory: 24.0K
      CPU: 109ms

Apr 05 10:47:39 jedi-2 systemd[1]: Starting LSB: mosquitto MQTT v3.1 message broker...
Apr 05 10:47:39 jedi-2 mosquitto[2621]:  * Starting network daemon: mosquitto
Apr 05 10:47:39 jedi-2 mosquitto[2621]:    ...done.
Apr 05 10:47:39 jedi-2 systemd[1]: Started LSB: mosquitto MQTT v3.1 message broker.
Apr 05 10:53:12 jedi-2 systemd[1]: Stopping LSB: mosquitto MQTT v3.1 message broker...
Apr 05 10:53:12 jedi-2 mosquitto[2823]:  * Stopping network daemon: mosquitto
Apr 05 10:53:12 jedi-2 mosquitto[2823]:    ...done.
Apr 05 10:53:12 jedi-2 systemd[1]: Stopped LSB: mosquitto MQTT v3.1 message broker.
```

To start the Mosquitto Broker service, use the command ```sudo /etc/init.d/mosquitto start```  

```
$ sudo /etc/init.d/mosquitto start
[ ok ] Starting mosquitto (via systemctl): mosquitto.service.
```
```
$ sudo /etc/init.d/mosquitto status
● mosquitto.service - LSB: mosquitto MQTT v3.1 message broker
   Loaded: loaded (/etc/init.d/mosquitto; bad; vendor preset: enabled)
   Active: active (running) since Thu 2018-04-05 10:53:23 CEST; 2s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2823 ExecStop=/etc/init.d/mosquitto stop (code=exited, status=0/SUCCESS)
  Process: 2871 ExecStart=/etc/init.d/mosquitto start (code=exited, status=0/SUCCESS)
    Tasks: 1
   Memory: 636.0K
      CPU: 13ms
   CGroup: /system.slice/mosquitto.service
           └─2878 /usr/sbin/mosquitto -c /etc/mosquitto/mosquitto.conf

Apr 05 10:53:23 jedi-2 systemd[1]: Starting LSB: mosquitto MQTT v3.1 message broker...
Apr 05 10:53:23 jedi-2 mosquitto[2871]:  * Starting network daemon: mosquitto
Apr 05 10:53:23 jedi-2 mosquitto[2871]:    ...done.
Apr 05 10:53:23 jedi-2 systemd[1]: Started LSB: mosquitto MQTT v3.1 message broker.

```

### Mosquitto broker configuration file

you can find details for the service, such as the log file in the configuration file for the Mosquitto broker:  

```
$ more /etc/mosquitto/mosquitto.conf
# Place your local configuration in /etc/mosquitto/conf.d/
#
# A full description of the configuration file is at
# /usr/share/doc/mosquitto/examples/mosquitto.conf.example

pid_file /var/run/mosquitto.pid

persistence true
persistence_location /var/lib/mosquitto/

log_dest file /var/log/mosquitto/mosquitto.log

include_dir /etc/mosquitto/conf.d
```

### Install the mosquitto-clients

install the ```mosquitto-clients``` package to then easily test MQTT through a couple of commands:
  - ```mosquitto_pub```: publish messages to the Mosquitto MQTT Broker to a specific Topic.
  - ```mosquitto_sub```: subscribe to a Topic to receive messages from the Mosquitto MQTT Broker.

```
$ sudo apt-get install mosquitto-clients
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libc-ares2 libmosquitto1
The following NEW packages will be installed:
  libc-ares2 libmosquitto1 mosquitto-clients
0 upgraded, 3 newly installed, 0 to remove and 66 not upgraded.
Need to get 144 kB of archives.
After this operation, 336 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc-ares2 amd64 1.10.0-3ubuntu0.2 [34.1 kB]
Get:2 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial/main amd64 libmosquitto1 amd64 1.4.15-0mosquitto1~xenial1 [54.6 kB]
Get:3 http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu xenial/main amd64 mosquitto-clients amd64 1.4.15-0mosquitto1~xenial1 [55.6kB]
Fetched 144 kB in 0s (1,140 kB/s)
Selecting previously unselected package libc-ares2:amd64.
(Reading database ... 60232 files and directories currently installed.)
Preparing to unpack .../libc-ares2_1.10.0-3ubuntu0.2_amd64.deb ...
Unpacking libc-ares2:amd64 (1.10.0-3ubuntu0.2) ...
Selecting previously unselected package libmosquitto1:amd64.
Preparing to unpack .../libmosquitto1_1.4.15-0mosquitto1~xenial1_amd64.deb ...
Unpacking libmosquitto1:amd64 (1.4.15-0mosquitto1~xenial1) ...
Selecting previously unselected package mosquitto-clients.
Preparing to unpack .../mosquitto-clients_1.4.15-0mosquitto1~xenial1_amd64.deb ...
Unpacking mosquitto-clients (1.4.15-0mosquitto1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up libc-ares2:amd64 (1.10.0-3ubuntu0.2) ...
Setting up libmosquitto1:amd64 (1.4.15-0mosquitto1~xenial1) ...
Setting up mosquitto-clients (1.4.15-0mosquitto1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
```

### Test the Mosquitto MQTT Broker

With the installation of both the Mosquitto Broker and clients, you can test that messages can be both published to and consumed.  

First, in one console window, subscribe to a Topic called "juniper", as follows:

```
$ mosquitto_sub -h localhost -t "juniper"

```
Next, using another console window, let’s publish a message to the "juniper" Topic, as follows:
```
$ mosquitto_pub -d -h localhost -t "juniper" -m "Hello World!"
Client mosqpub|2811-jedi-2 sending CONNECT
Client mosqpub|2811-jedi-2 received CONNACK
Client mosqpub|2811-jedi-2 sending PUBLISH (d0, q0, r0, m1, 'juniper', ... (12 bytes))
Client mosqpub|2811-jedi-2 sending DISCONNECT
```
Now return back to first console (that subscribed to the “juniper” topic).  You can see the published “Hello World!” message (published by the second console)  
```
$ mosquitto_sub -h localhost -t "juniper"
Hello World!
```

### Credits 
All the credits go to https://techmocha.blog/2018/03/29/streaming-junos-telemetry-to-mqtt-via-telegraf/
