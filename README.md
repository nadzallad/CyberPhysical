# robotics-turtlebot3

Syarat: Docker Engine >= 24 dan Docker Compose >= v2.20. ROS tidak perlu dipasang di host.

```bash
git clone https://github.com/nadzallad/CyberPhysical.git
cd robotics-turtlebot3/docker
docker compose build
docker compose up
```

Hasil: node `talker` dan `listener` berjalan otomatis dan saling bertukar pesan.

Untuk menjalankan package sendiri dalam mode development:

```bash
docker compose --profile dev run --rm dev
colcon build --symlink-install
source install/setup.bash
ros2 run my_first_robot_package hello_robot
```

Output yang diharapkan:

```text
Hi from my_first_robot_package.
```
