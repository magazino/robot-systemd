# robot-systemd

Debian package for auto-starting a ROS launch files with systemd using
systemd_ros.

## How to use it

Adapt ``/etc/ros/robot-bringup`` according to the needs of your robot:


| Key    			| Default   		| Description 																								  |
| ----------- | ------------- | ------------------------------------------------------------- |
| PACKAGE			| robot_bringup | Name of the ROS package which contains the main launch file 	|
| LAUNCH_FILE	| robot.launch 	| Name of the launch file within the above mentioned PACKAGE		|
| SERVICE 		| robot-bringup | Name of the generated systemd service.												|
| USER	 			| robot 				| Linux User which is used to start the services								|
| GROUP 			| robot					| Linux Group which is used to start the services								|


## Adding extra service parameters

The file ``/etc/ros/robot-bringup-extras.yaml`` can be used to configure
additional
[Service](https://www.freedesktop.org/software/systemd/man/systemd.service.html) 
and 
[Unit](https://www.freedesktop.org/software/systemd/man/systemd.unit.html) 
parameters for each ROS node.

In the following example we make sure that the ``/talker`` node is started with
``CPUWeight`` set to ``200``.

```yaml
/talker:
    Service:
        CPUWeight: 200
```
