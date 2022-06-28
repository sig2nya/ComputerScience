Docker로 MySQL 실행
===================
* 1) docker run -it --name mysql -e MYSQL_ROOT_PASSWORD=Avaya123$ -e MYSQL_DATABASE=dockerdb mysql 명령어 수행
     <img width="626" alt="image" src="https://user-images.githubusercontent.com/70207093/176130654-3e7b95b8-dc3a-4d7d-8045-9affe3551331.png">

* 2) 새로운 Terminal 창 -> docker ps</br>
     <img width="716" alt="image" src="https://user-images.githubusercontent.com/70207093/176130856-2cce1df2-d1c7-4aff-baf5-0480c3985c81.png">

* 3) Container exec</br>
     <img width="722" alt="image" src="https://user-images.githubusercontent.com/70207093/176131272-8d2e680e-7f02-4072-88a5-6b1862ada89a.png">

* 4) Terminal을 통한 MySQL 접속</br>
     <img width="720" alt="image" src="https://user-images.githubusercontent.com/70207093/176131689-2e845170-3e1a-487e-b7ef-d1b50cb104d3.png">

* 5) Test용 DB를 만들어 주었다.</br>
     <img width="722" alt="image" src="https://user-images.githubusercontent.com/70207093/176131858-453a50c1-4be9-4f8d-b5d7-6135a0f70a49.png">

* 이제 해당 DB에 접속하는 방법을 찾아야 할 것 같다.
 
Docker MySQL NetWork Configuration
==================================
* 1) docker container inspect [container name]
```java
[
    {
        // * 생략 * //
        "Created": "2022-06-28T08:20:08.876432828Z",
        "Path": "docker-entrypoint.sh",
        "Args": [
            "mysqld"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 4612,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2022-06-28T08:20:09.502986845Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:0ef9083d9892db139e2b7c81fd133836e7aa32db2b5f1d5702e2593100fa1417",
        "ResolvConfPath": "/var/lib/docker/containers/5de41e86dff50ffd32973449feda8c1b045c26beafb7fe67ca335a81f7b972cc/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/5de41e86dff50ffd32973449feda8c1b045c26beafb7fe67ca335a81f7b972cc/hostname",
        "HostsPath": "/var/lib/docker/containers/5de41e86dff50ffd32973449feda8c1b045c26beafb7fe67ca335a81f7b972cc/hosts",
        "LogPath": "/var/lib/docker/containers/5de41e86dff50ffd32973449feda8c1b045c26beafb7fe67ca335a81f7b972cc/5de41e86dff50ffd32973449feda8c1b045c26beafb7fe67ca335a81f7b972cc-json.log",
        "Name": "/mysql",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/03d4bfe0829b6fb20d75b79b19330b93b1cf0b1b665abeb5379f2e1851ba97ce-init/diff:/var/lib/docker/overlay2/270bf185c53271568470397ebe20d1b0d3db8d4a6785c401fee6c910c3adbb7c/diff:/var/lib/docker/overlay2/db415123471690b15f7c005bfe5af8dabe3ee4de65e2755a8bcccdf5e5d03b79/diff:/var/lib/docker/overlay2/0fac01240b5105b328c17d50f786049d2e97026c8f62d8f27f779de8f71a59f9/diff:/var/lib/docker/overlay2/c287b5d6af8dd53d26ec7aaed9c29e101417520e8c6116131a025028d734bc82/diff:/var/lib/docker/overlay2/7c9027f3f14431f24fcaed59e78f3d2759ce1f606ef5ba6aea25ff25103c4b08/diff:/var/lib/docker/overlay2/213654a03dfec7fa1442252db5503d005e9a9744f53f3a9b1439e092dad04842/diff:/var/lib/docker/overlay2/528ce4176870abeb90e33fc4aaa9351d9f3aaa15a7704f51b2fd2832add6f3c7/diff:/var/lib/docker/overlay2/b9a5e66e5f796216be28baec12b6fc29ca6dda378e88e7be6f9111c7f73db191/diff:/var/lib/docker/overlay2/d3a7421f26d3112c650bba52ad6567b6aef35c0d1b9557f6277ba5ef58491a51/diff:/var/lib/docker/overlay2/cf978ce863f1d863a5caaa5ead6e11bda01956269b4a953a9953fd2cd64556b3/diff:/var/lib/docker/overlay2/951da937f84e2e8ba349c6c7f6e253d328e2631b4be3cf246977a83e01f843ab/diff:/var/lib/docker/overlay2/b6bf543f8463f19f9f2d506c10d714f41a585cf239481d6995448c33aaaa30e4/diff",
                "MergedDir": "/var/lib/docker/overlay2/03d4bfe0829b6fb20d75b79b19330b93b1cf0b1b665abeb5379f2e1851ba97ce/merged",
                "UpperDir": "/var/lib/docker/overlay2/03d4bfe0829b6fb20d75b79b19330b93b1cf0b1b665abeb5379f2e1851ba97ce/diff",
                "WorkDir": "/var/lib/docker/overlay2/03d4bfe0829b6fb20d75b79b19330b93b1cf0b1b665abeb5379f2e1851ba97ce/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [
            {
                "Type": "volume",
                "Name": "567f9191b870e7ac07ef07e2a1102ea95e5a125b457d42c7d48663f604d12b97",
                "Source": "/var/lib/docker/volumes/567f9191b870e7ac07ef07e2a1102ea95e5a125b457d42c7d48663f604d12b97/_data",
                "Destination": "/var/lib/mysql",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
        "Config": {
            "Hostname": "5de41e86dff5",
            "Domainname": "",
            "User": "",
            "AttachStdin": true,
            "AttachStdout": true,
            "AttachStderr": true,
            "ExposedPorts": {
                "3306/tcp": {},
                "33060/tcp": {}
            },
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": true,
            "Env": [
                // * 생략 * //
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "GOSU_VERSION=1.14",
                "MYSQL_MAJOR=8.0",
                "MYSQL_VERSION=8.0.29-1debian10"
            ],
            "Cmd": [
                "mysqld"
            ],
            "Image": "mysql",
            "Volumes": {
                "/var/lib/mysql": {}
            },
            "WorkingDir": "",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "eb7464bd105aaa33329277b14bc0ef6bfca4da5fd133981f58ae9dedf9a08adb",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "3306/tcp": null,
                "33060/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/eb7464bd105a",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            // * 생략 * //
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            // * 생략 * //
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            // * 생략 * //
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    // * 생략 * //
                    // * 생략 * //
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    // * 생략 * //
                    "DriverOpts": null
                }
            }
        }
    }
]
```

* 참으로 역겨운 JSON이다. 이제 해당 컨테이너를 macvlan에 연결해보자.

* 2) docker attach mysql 했는데 뭔가 반응이 없다.</br>
     <img width="626" alt="image" src="https://user-images.githubusercontent.com/70207093/176134028-fd0fb814-b256-49f0-8ddb-2de3fa8f5cf0.png">

