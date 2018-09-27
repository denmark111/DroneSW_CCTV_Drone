# General
## SublimeText Example
```
aaa
bbb
cccc

ctl+a → ctl+shift+l → " → end
   → del → , → end → BackSpace → ctl+a → [
```

## Datafile Format
1. csv
```
id,name
1,aaa
2,bbb
3,cccc
```

2. json
* List : []
* Dictionary : {}
```
[
{"id":1,"name":"aaa"},
{"id":2,"name":"bbb"},
{"id":3,"name":"cccc"}
]


{
  "id":[1,2,3],
  "name":["aaa","bbb","cccc"]
}
```

3. XML
```
<xml>
    <row>
        <id>1</id>
        <name>aaa</name>
    </row>
    <row>
        <id>2</id>
        <name>bbb</name>
    </row>
    <row>
        <id>3</id>
        <name>cccc</name>
    </row>
</xml>
```

# info
## Simulator
* 흉내만 냄.
* ex) Docker

## Emulator
* Cpu단위에서 100%구현...
* ex) VM

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

# Makrdown

## makrdown
 ![](http://j.finfra.com/d/lib/exe/fetch.php?tok=a08f3d&media=http%3A%2F%2Fj.finfra.com%2Fd%2F_img%2FNamJungGu-kbs9news.jpg)
 <http://chenluois.com>,

 [Mou](https://twitter.com/mou)

 [a relative link](other_file.md)


 [^1]: And that's the footnote.

 ![Smaller icon](http://25.io/smaller/favicon.ico "Title here")

* table
|id|name |
|--|-----|
|1 |aaa  |
|2 |bbb  |
|3 |cccc |

# Python 기본
## 중요 명령어
* import
* dir()
* help()

## import 3가지 스타일
```
import math
print math.pi

from math import pi
print pi

from math import pi as p
print p
```

## 필수 해더
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```


## 모듈검색
```
import math
print('\n'.join([m for m in dir(math) if not callable(getattr(math,m))]))
print('\n'.join([s for s in dir(math) if s.find('co') >= 0 ]))
print('\n'.join([s for s in dir(math) if s.upper().find('co'.upper()) >= 0 ]))
```

## Python Library
### 분석용
```
from csv,db,json,xml
↓
pandas로 로딩해서 가공
↓
numpy로 전처리
↓
모델을 만듦
↓
Seaborn이나 matboltlib로 시각화
```

## Python3 설치 방법(Jupyter가능하게)
* OS 전체
```GuestOS
apt install -y python3 python3-pip
pip3 install ipykernel
python3 -m ipykernel install --user --name=Python3
pip3 install tensorflow pandas
```
```HostOS
docker commit t1 tensorflow/tensorflow:0.4
```


## Python VirtualEnv
* http://dlwiki.finfra.com/base_study:virtualenv_with_jupyter
* 셋팅
```
pip3 install virtualenv virtualenvwrapper
cat >>~/.bashrc<<EOF
export WORKON_HOME=~/.virtualenvs
. /usr/local/bin/virtualenvwrapper.sh
EOF
rm /usr/bin/python
ln -s /usr/bin/python3 /usr/bin/python
. ~/.bashrc
```
* 가상환경 리스트 보기
workon

* 만들기 
mkvirtualenv py3

* 나가기
deactivate

* 활성화 
workon
workon 환경이름


* jupyter 가능하게 하기
mkvirtualenv py3
pip3 install ipykernel jupyter
python -m ipykernel install --user --name=py3


```HostOS
docker commit t1 tensorflow/tensorflow:0.5
```

* Web Service Test용  
```
docker rm -f t1;docker run      \
    -it                         \
    -p 8888:8888                \
    -p 8000:8000                \
    -p 8080:8080                \
    -v ~/df:/notebooks/df       \
    --name=t1                   \
tensorflow/tensorflow:0.3
```

## pydoc사용
```
1. 코딩+주석
2. pydoc -p 8080
3. links를 설치 : apt-get install -y links  (안되면 apt-get update )
4. links http://localhost:8080
5. /라이브러리명 → enter
```




.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI4MjQwMTg3Ml19
-->