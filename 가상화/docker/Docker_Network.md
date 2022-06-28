* 참고 :
* * https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=alice_k106&logNo=220984112963 
* * https://jonnung.dev/docker/2020/02/16/docker_network/

Docker 네트워크 종류
===================
* 1) Ubuntu의 Network Interface 확인을 위해 ifconfig / 명령어가 먹지 않는다면, install 수행해주자.
     <img width="626" alt="image" src="https://user-images.githubusercontent.com/70207093/176111780-3337b4a9-4ae1-45dc-b94b-18033b3ac10f.png">

* 2) Docker Network Interface를 확인 가능. docker0는 일반적인 가상 인터페이스가 아니며 도커 자체적으로 제공
     <img width="431" alt="image" src="https://user-images.githubusercontent.com/70207093/176112271-80c3fdec-1470-496a-9509-70e9254fca15.png">

* 3) 도커에서 사용할 수 있는 네트워크 종류는 브리지(bridge), 호스트(host), 논(none)
     <img width="628" alt="image" src="https://user-images.githubusercontent.com/70207093/176111445-9e795ef4-632a-4316-af88-e986b1fd5e9e.png">

* 4) docker network inspect bridge 명령어 수행
```java
[
    {
        "Name": "bridge",
        // ... 생략 ... //
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        // ... 생략 ... //
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        },
        "Labels": {}
    }
]
```

* * Docker는 172.17.0.0/16 대역의 IP를 순차적으로 할당. 컨테이너는 외부와 통신하기 위해 2개의 네트워크 인터페이스를 함께 생성한다.
* * 하나는 컨테이너 내부 Namespace에 할당되는eth0 이름의 인터페이스이고, 나머지 하나는 호스트 네트워크 브리지 docker0에 바인딩 되는 vethXXXXXXX이름 형식의 veth 인터페이스다. 
* * (“veth”는 “virtual eth”라는 의미)

![image](https://user-images.githubusercontent.com/70207093/176114380-7954a1ba-ae44-4ad0-bcb1-a75da5dc7664.png)
