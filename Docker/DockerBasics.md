# Docker

|명령 예                                                  | 설명                    |
|---------------------------------------------------------|-------------------------|
|docker search ubuntu                                     |이미지 찾기              |
|docker run -it  --name u1 ubuntu                         |u1이름으로 ubuntu 실행   |
|docker run -it --name u1 -v ~/df:/df  ubuntu             |추가 저장폴더 설정       |
|docker run -it --name u1 -v ~/df:/df -p 8888:8888 ubuntu |입,출 포트포워딩 설정    |
|docker ps -a                                             |모든 컨테이너 리스트     |
|docker start u1                                          |u1 시작                  |
|docker attach u1                                         |u1 동기화접속            |
|docker exec -it u1 bash                                  |u1 개별 사용 접속        |
|docker rm -f u1                                          |u1 최고권한 종료         |
|docker commit  u1 ubuntu:0.1                             |작업내용 통합저장        |
|docker images                                            |모든 이미지 보기         |
|docker save -o  ubuntu0.1.docker  ubuntu:0.1             |이미지 파일로 내보내기   |
|docker load -i ubuntu0.1.docker                          |파일로부터 이미지 만들기 |
|docker pull tensorflow/tensorflow                        |이미지만 미리 받기       |

```
cd
mkdir ~/df
docker rm -f t1;docker run      \
    -it -p 8888:8888            \
    -v ~/df:/notebooks/df       \
    --name=t1                   \
tensorflow/tensorflow
```
docker native일때
toolbox일때는 192.168.99.100
∵ virtual box의 ip
  from "docker-machine ip"


*
* 복붙 가능하게,
docker Quick Start Terminal에서
왼쪽 위의 창 아이콘 누르면!
  속성→빠른 편집모드 체크 하세요.
     그래야 복·붙이 돼요....
* 일명 도스창에서 복붙은? 마우스 오른쪽 버튼으로....