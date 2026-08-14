# canboat_vendor

This is a wrapper around the [Canboat repository](https://github.com/canboat/canboat) for building with ROS 2's Colcon.

## How to use

1.  ```
    colcon build --packages-select canboat_vendor
    ```

2.  ```
    ros2 run canboat_vendor <any executable built by the Canboat repository>
    ```

3.  Available executables are:
    - `actisense-serial`
    - `analyzer`
    - `analyzer-j1939`
    - `candump2analyzer`
    - `command-group-function`
    - `ikonvert-serial`
    - `iptee`
    - `maretron-ipg`
    - `nmea0183-serial`
    - `replay`
    - `request-group-function`
    - `socketcan-serial`
    - `socketcan-writer`
