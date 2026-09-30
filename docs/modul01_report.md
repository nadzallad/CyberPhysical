Laporan Modul 01

## Langkah yang Dikerjakan

1. Memastikan Docker Engine dan Docker Compose dapat digunakan pada host.
2. Menjalankan image `ros:humble-ros-base-jammy` dan memastikan ROS 2 dapat dijalankan di dalam container.
3. Membuat workspace `robotics-turtlebot3` beserta struktur folder `docker`, `src`, dan `docs`.
4. Membuat package ROS 2 `my_first_robot_package` dengan node `hello_robot`.
5. Membuat `docker/Dockerfile`, `docker/entrypoint.sh`, dan `docker/compose.yaml`.
6. Membuat image Docker menggunakan `docker compose build`.
7. Menjalankan service `talker` dan `listener` menggunakan `docker compose up`.
8. Memeriksa komunikasi ROS 2 menggunakan `ros2 node list` dan `ros2 topic echo /chatter --once`.
9. Memastikan node `/talker` dan `/listener` berjalan dan pesan `Hello World` berhasil diterima.
10. Menjalankan mode development menggunakan `docker compose --profile dev run --rm dev`.
11. Melakukan `colcon build --symlink-install` dan menjalankan package dengan:
    `ros2 run my_first_robot_package hello_robot`.
12. Membuat repository Git, menghubungkannya dengan repository GitHub kelompok, serta melakukan push ke branch `main`.
13. Membuat `README.md` dan laporan praktikum pada `docs/modul01_report.md`.

## Hasil

Docker berhasil digunakan sebagai lingkungan pengembangan ROS 2 Humble tanpa perlu memasang ROS 2 secara langsung pada host.
Node `talker` berhasil melakukan publishing pesan pada topic `/chatter`, sedangkan `listener` berhasil menerima pesan. Hasil pengecekan node menunjukkan:
/listener
/talker

Package `my_first_robot_package` juga berhasil di-build dan dijalankan dengan output:

Hi from my_first_robot_package.

Repository berhasil di-push ke GitHub dan telah memiliki minimal tiga commit bermakna.

## Masalah yang Ditemui

Selama praktikum, terdapat beberapa kendala yang ditemui. Pada awal proses, folder ~/robotics-turtlebot3/docker belum tersedia sehingga perlu membuat workspace dan struktur folder terlebih dahulu. Saat membuat package ROS 2 dengan user host, terjadi error KeyError: 'getpwuid(): uid not found: 1000'. Masalah tersebut kemudian diselesaikan dengan menambahkan environment USER dan HOME pada container. Selain itu, Dockerfile sempat dimasukkan dan dijalankan langsung melalui terminal sehingga perintah seperti FROM, RUN, dan COPY dianggap sebagai command Linux. Masalah ini diperbaiki dengan menyimpan konfigurasi tersebut ke dalam file docker/Dockerfile. File compose.yaml juga sempat mengalami kesalahan konfigurasi YAML karena terdapat key yang terduplikasi, sehingga docker compose build gagal dijalankan dan perlu diperbaiki terlebih dahulu. Pada tahap koneksi repository, proses git push sempat mengalami error 403 karena masalah autentikasi GitHub. Masalah tersebut kemudian diselesaikan dengan menggunakan Personal Access Token (PAT) yang memiliki izin untuk melakukan push ke repository. Setelah permasalahan tersebut diselesaikan, proses build, komunikasi node ROS 2, build package, dan push repository berhasil dilakukan.
