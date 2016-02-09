Access control reporting system
====

## Set up dev host

#### To start application host:

```bash
cd ops/application-host
vagrant up
```

**Known problems:**
* Re-provision will be failed

#### To destroy application host:

```bash
cd ops/application-host
vagrant destroy -f
```

## Build

On UNIX-like operating systems, the following Bash shell command will enable the Daemon for the current user:

```bash
touch ~/.gradle/gradle.properties && echo "org.gradle.daemon=true" >> ~/.gradle/gradle.properties
```

Full build

```bash
gradle clean build
```

## Demo 
* Test data located at: `test-data/visit.txt`
* Row data foramat :`UUID,UUID,yyyy-MM-dd HH:mm:ss,yyyy-MM-dd HH:mm:ss`

We can update `test-data/visit.txt`

To load `test-data/visit.txt` into system:

- Login to application-hos:
```bash
cd ops/application-host
vagrant ssh
```
- run demo provision script in application-host:
```bash
sh /application-host/ops/demo-provision.sh
```

**Known problems:**
* Re-provision can be failed

## Available links

* To get status of application go to [Supervisor](http://localhost:9000/)
* To run data import go to [Run import thru Supervisor](http://localhost:9001/index.html?processname=data%3Aimport&action=start)
* To run data analytic go to [Run analytic thru Supervisor](http://localhost:9001/index.html?processname=data%3Aanalytic&action=start)
* To show report go to [Access control Dashboard](http://localhost:9999/)
* Mater Redis run at localhost:6000

* Application server:
 * [Supervisor](http://localhost:9000/)
 * [Access control Dashboard](http://localhost:9999/)
 * [Reporting api instance](http://localhost:9999/api/)
 * [Mater Redis commander](http://localhost:6100/)
* Application slaves:
 * Slaves #1
  * [Supervisor for slaves #1](http://localhost:9001/)
  * [Redis Slave #1 commander](http://localhost:6101/)
  * [Reporting api instance #1](http://localhost:9901/manage/health)
 * Slaves #2
  * [Supervisor for slaves #2](http://localhost:9002/)
  * [Redis Slave #2 commander](http://localhost:6102/)
  * [Reporting api instance #2](http://localhost:9902/manage/health)
