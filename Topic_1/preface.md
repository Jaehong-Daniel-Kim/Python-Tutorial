# Topic 1:

Topic 1, 본 페이지에서는 Python의 가장 기본적인 정보와 지식에 대하여 서술한다.  
아래 Python설치 방법이나, pypi-server 설치 및 구축 방법 그리고 virtual environemnt(가상환경)을 사용하는 내용은  
모른다고 하여도 Python을 사용하는데 아무런 지장이 없고, 자격증 시험을 볼 때에도 필요한 내용은 아니다.

하지만, 지금하지 않아도 Python을 계속 활용한다면 언젠가는 한번쯤 대면해야할 토픽인것은 확실하다.
***
# Table of Contents
1. [Planning for final project](#1-planning-for-final-project)
2. [Python Installation](#2-python-installation)
3. [PIP](#3-pip-pip-installs-packages)
4. [Virtual Environment](#4-virtual-environment)

***
## 1. Planning for Final Project
아래 질문에 대한 답변을 생각하는 시간을 갖고, 추후 진행될 프로젝트에 대한 계획 수립하기.


- 만들고자 하는 프로그램의 목적은 무엇인가?
  - 예1) 데이터를 자동으로 취합하여 필요한 데이터만 화면에 출력해주는 프로그램.
  - 예2) 특정 상태, 데이터 등을 자동으로 모니터링 해주는 프로그램.
- 해당 프로그램을 사용하므로써 성취하고자 하는 목표는 무엇인가? 
  - 예1) 평소 수작업으로 1시간 소요되는 작업을 수초, 수분만에 간편하게 끝낼 수 있다. 
  - 예2) 업무가 바쁠 시 놓칠 수 있는 부분을 자동으로 모니터링 하여 빠른 이슈 대응 및 필요 시 빠른 조치가 가능하다.
- 해당 프로그램을 작성하기 위해서 필요한 기능은 무엇인가?
  - 예1) Data Source로 부터 데이터를 취합하는 기능, 데이터 전처리 기능, 필요한 데이터만 출력하는 기능
  - 예2) Data Source로 부터 데이터를 취합하는 기능, 필요한 부분을 확인 하여 문제가 발생 여부를 판단하는 기능, 문제 발생 시 알람 기능
- 해당 프로그램을 실행하기 위하여 얼마나 많은 resource가 필요할것이라 예상하는가?
  - 예1) 데이터를 취합하기 위하여 리눅스 커맨드를 10번 이상 실행해야한다. 읽어오는 데이터가 많기 때문에 프로그램 내 메모리 사용률 높을것으로 예상된다. 
  - 예2) 여러 수백개의 호스트의 상태를 체크해야하는데 하나씩 체크하게되면 시간이 오래 소요될 것으로 예상하여 Multiprocessing을 계획하며, 최소 4개의 core를 사용할것으로 예상된다. 
- 해당 프로그램을 개발할 때 가장 힘들것이라 예상되는 부분은?
  - 예1) 많은 양의 데이터를 전처리 하는 부분에서 프로그램의 실행 속도가 걱정되며, 어떻게 해야 가독성 좋게 결과가 화면에 출력될지 고민된다. 
  - 예2) Multiprocessing을 구현하는 부분이 어려울것으로 예상된다. 

 

| 프로그램 예시                                           |
|:--------------------------------------------------|
| 데이터 소스로부터 데이터를 받아와서 전처리 후 필요한 데이터만 화면에 출력해주는 프로그램 |
| 방대한 양의 데이터 (로그파일) 등을 읽어 특정 키워드를 찾아주는 프로그램         |
| 사용자의 입력값을 받아와 특정 기능을 수행해주는 프로그램                   |
| 주특정 주기로 자동으로 모니터링 해주는 모니터링 프로그램                   |

***

## 2. Python Installation
사내 환경과 같이 인터넷접속이 어려운 환경에서는 Python을 수동으로 직접 설치를 해주어야 한다.  
하기 설치 과정을 참고하여 설치를 진행한다.

#### 1. Download Python
Online환경에서 http://python.org 로 접속하여 필요한파이선 버전을 다운로드 받는다. (예시에서는 3.9.13 버전을 기준으로 함.)
- 사이트 접속 -> Downloads -> Source Code -> Stable Releases -> Python 3.9.13 버전 찾기 -> tar.xz 또는 tar.gz 형태의 압축파일 다운로드
- FTP등을 활용하여 다운로드 받은 tarball 파일을 서버 내로 이동 (tar.gz, tar.xz 등 tar 포멧으로 패키징되어 압축되어 있는 파일 형태를 말한다.)

#### 2. Uncompress
tar.gz 또는 tar.xz형태로 압축되어있는 파일을 모두 아래 명령어를 공통으로 사용하여 압축을 해제할 수 있다.
```shell
tar xf <PYTHON_TARBALL_PATH> --directory <DESTINATION_DIR>

# PYTHON_TARBALL_PATH: Python이 설치되어있는 위치
# DESTINATION_DIR: 압축이 해제된 파일이 저장될 위치
```

#### 3. Compile
아래 커맨드를 사용하여 Python Source Code Compile 진행
```shell
cd <DESTINATION_DIR>/Python-3.9.13

./configure \
--prefix=<INSTALL_PATH> \  
--enable-shared \  
--enable-optimization \ 

# --prefix=<INSTALL_PATH>: # 설치 경로 설정  <INSTALL_PATH> = Python이 설치될 경로
# --enable-shared: Static(정적) 라이브러리와 Dynamic(동적) 라이브러리르 모두 built 함 해당 옵션이 없을 시 build과정에서 오류가 발생할 수 있음
```

#### 4. Installation (Build)
아래 커맨드를 사용하여 Python Source Code build 진행.
```shell
make  # Source Code Build
make install  # Build한 내용으로 설치 진행 prefix를 본인이 권한을 갖고있는 경로로 설정하였다면 sudo 권한 없이 설치 가능
```

#### 5. Set Environment Variables
설치한 Python을 Shell에서 정확하게 참조하려면 아래와 같이 환경변수 설정을 해주어야 한다.
```shell
# /bin/csh  # CShell 환경
# Python을 설치한 경로 하위의 bin/ 디렉토리를 PATH 환경번수 가장 상단에 설정
setenv PATH <INSTALL_PATH>/bin:$PATH  
# Python을 설치한 경로 하위의 lib/ 디렉토리를 LD_LIBRARY_PATH 환경변수 가장 상단에 설정
setenv LD_LIBRARY_PATH <INSTALL_PATH>/lib:$LD_LIBRARY_PATH  
```

#### 6. Check 
```shell
# 경로 설정 확인, Python을 설치한 경로 하위의 Python이 나와야 함.
which python3  # should return: <INSTALL_PATH>/bin/python3

# 버전 확인, 설치한 버전이 출력되어야 함
python3 version # should return: 3.9.13

# Library 설정 확인, LD_LIBRARY_PATH 설정이 제대로 되었다면 정상 실행되어야 함.
python3  # should start Python console
```

***

## 3. PIP (PIP Installs Packages)
PIP란 "PIP Installs Packages"의 준말로, Red Hat계열의 `yum` 또는 Debian 계열의 `apt`와 같은 패키지 매니저이다.  
- 단일 패키지 파일을 개별로 설치할 수 있지만, 이 경우 모든 의존성 패키지 또한 개별로 설치해주어야 한다.  
- 위와 같은 의존성 문제를 해결하기 위하여 pypi-server를 구축해서 사용할 필요가 있다.
- pypi-server를 구축하게 되면, 해당 서버의 repo(repository)내 존재하는 파일을 서버가 관리하여, 특정 패키지를 설치할 때 관련 의존 패키지도 함께 한번에 설치할 수 있다.

#### 1. Install pypi-server
인터넷 접속이 가능한 환경에서 https://pypi.org 페이지로 접속한다
- pypiserver 검색 후 pypiserver >= 2.0.1 (pypiserver 2.0.1 버전 이상)을 찾아서 클릭 (보통 가장 상단에 나온다)
- 좌측 Navigation에서 Download files로 이동
- Build Distribution 섹션에서 본인이 사용하는 Python버전과 사용중인 architecture에 맞는 패키지 버전을 다운로드 
  - ...py2.py3-none-any.whl과 같은 형식은 python2 버전과 python3 모든 버전에서 호환 되며, 특정 architecture에 귀속되지 않는 패키지 이다
- FTP등을 활용하여 서버 내로 패키지 파일을 이동
> 위 과정에서 pypi-server를 찾지 못할 경우 아래 경로로 이동  
> https://pypi.org/project/pypiserver/

위 준비 과정이 완료 되었다면 아래와 같은 커맨드를 사용하여 패키지를 설치할 수 있다.
```shell
# pip3 경로 확인, Python을 설치한 경로 하위의 pip3가 나와야 함.
which pip3  # should return: <INSTALL_PATH>/bin/pip3

# pip를 활용한 pypi-server package 설치
pip3 install <PACKAGE_PATH>/pypiserver-2.0.1-py2.py3-none-any.whl  # pypiserver 패키지가 위치한 경로 입력
# 설치 완료 메시지 확인
# ...
# Installing collected packages: pypiserver
# Successfully installed pypiserver-2.0.1

# 설치 확인, Python을 설치한 경로 하위의 pypi-server가 나와야 함.
which pypi-server  # should return: <INSTALL_PATH>/bin/pypi-server
```
pip 사용 시 만약 아래와 같은 warning이 발생한다면, 현재 사용하고있는 pip의 버전이 낮아서 발생하는 것이다.
> WARNING: You are using pip version 22.0.4; however, version 24.0 is available.  
> You should consider upgrading via the '<PYTHON_INSTALLED_PATH>/bin/python3.9 -m pip install --upgrade pip' command.  

이 경우 위와 동일한 방볍으로 https://pypi.org 페이지를 통하여 pip버전을 업데이트 해줄 수 있다. 
- 온라인 환경에서는 warning 메시지에 나오는 커맨드를 사용하여 바로 업데이트가 가능
- 하지만 오프라인 환경에서는 항상 수동으로 위의 과정을 거쳐야 한다. 

#### 2. Run pypi-server
Pypi server를 시작하기 위해서는 repo(repository)경로를 생성 및 지정이 선행 되어야만 한다.  
아래 커맨드를 참조
```shell
# repository경로 생성
mkdir $HOME/packages  # repository 경로는 아무 경로나 편한대로 설정 가능
# pypi-server 실행
pypi-server run -p 3000 $HOME/packages & 
# -p: 포트 설정, 이미 예약된 포트가 아니라면 아무 포트나 사용 가능
# $HOME/packages:  repository 경로 설정
# &: 백그라운드로 실행
```
위 과정까지 완료 되었다면 firefox와 같은 인터넷 브라우저를 실행한 후 http://localhost:3000으로 접속해자.  
"Welcome to pypiserver!" 화면이 보인다면 실행에 성공한 것이다.

#### 3. Configure pip.conf
Pypi-server 설치가 완료 되었다면 아래와 같이 pip.conf 파일을 설정 해주어야 한다.
```pip.conf
# $HOME/.pip/pip.conf

[global]
timeout = 60
index-url = http://<HOST_NAME_OR_ADDRESS>:<PORT>
trusted-host =
    <HOST_NAME_OR_ADDRESS>


# 예시)
[global]
timeout = 60
index-url: http://my-host:3000
trusted-host = 
    my-host
```
pip.conf 파일 설정까지 완료 되었다면 이제 설정한 packages/ 디렉토리에 python관련 패키지를 넣고 `pip3 install <패키지 명>` 커맨드로 바로 설치할 수 있다. 

***
## 4. Virtual Environment
Virtual Machine등 서버 가상머신을 생성하듯, 파이썬 또한 가상 환경을 만들어 사용할 수 있다.  
가상 환경의 역할은 하나의 동일 호스트 내에서 프로젝트별로 독립적인 Python개발 환경을 만들어 주어 독립적으로 Python 버전, 패키지 등을 관리할 수 있도록 해준다.  
아래와 같은 상황에서 유용하게 사용될 수 있다.  

-  하나의 서버를 10명의 사용자가 사용한다고 가정하였을 때, 10명의 사용자는 각자의 디렉토리에 각자 Python을 설치하여 사용 
    - 10명 모두 동일 버전의 Python을 사용한다고 가정하였을 때, 불필요한 저장 공간이 낭비되며,
서로 코드를 공유할 시 패키지의 버전이 호환되지 않아 오류가 발생할 가능성이 있다.
 
- 한 유저가 여러 Project에서 다양한 버전의 Python을 사용해야 하는 경우
  - 해당 유저는 매번 각각의 프로젝트에서 PATH, LD_LIBRARY_PATH등을 설정 해주어야 하는 등, 
개발환경, 실행 환경을 구축하기에도 불필요한 요소가 많이 발생된다.
 
- 코드를 배포할 경우
  - 프로그램을 작성 후 배포할 경우 사용한 Package를 requirement.txt 파일에 정리하곤 한다.
하지만 하나의 Python에 다른 여러 프로젝트에서 사용한 다양한 패키지가 설치되어 있다면, 특정 프로젝트마다 사용한 패키지를 설별하기 어렵다.
  - > pip3 freeze를 입력하게되면 현재 환경에 설정되어있는 Python에 설치되어있는 모든 패키지를 확인할 수 있다.   
    하지만 다른 프로젝트에서 사용한 패키지가 모두 한곳에 설치되어 있다면 특정 프로젝트에 사용된 패키지만 설별하여 requirements.txt파일을 정리하기 어렵다.
    
위에 제시한 이유과 더불어 여러 다른 이유로 가상 환경을 만들어 사용하는 것을 적극적으로 권장하고 있다.  

#### 1. Python 가상환경 종류
Python에서 가상환경이 매우 유용하고 중요하기 때문에 Python 자체에는 `venv` 라는 가상환경을 만들어주는 패키지가 기본적으로 설치되었다.  
하지만 기본적인 `venv` 패키지보다 더 강력하고, 다양한 기능으 탑제한 외부 가상 환경 패키지가 많이 개발되었으며, 종류는 아래와 같다. 
- `pipenv`
- `virtualenv`
- `conda`
- `pyenv`
- `poetry`

각각의 가상환경 패키지마다 장단점이 있지만, 이 과정에서는 pipenv를 기준으로 사용할 예정이다.  
각 패키지는 모두 특성과 성격이 다르니 직접 리서치를 해보고, 이것저것 사용해보면서 직접 비교해 보는것도 좋다.

pipenv 공식 문서: https://pipenv.pypa.io/en/latest/
위 사이트에서 더 자세한 내용을 확인해볼 수 있다. 

pipenv는 대표적으로 아래와 같은 특징을 갖고 있다. 
- 가상환경을 생성해주는 툴(virtualenv)과 패키지 매니저(pip)를 따로 사용할 필요가 없다. 
- requirements.txt대신 Pipfile과 Pipfile.lock을 사용하여 더 체계적인 패키지 관리를 할 수 있다.  
- 패키지 설치와 동시에 Pipfile.lock (lock file)파일에 hash가 함께 저장되어 보안성을 높여준다. 
- `pipenv graph`커맨드를 활용하여 패키지 의존성에 대한 정보를 쉽게 파악할 수 있다.


#### 2. pipenv Installation 

위 pip 섹션을 참고하여 동일한 방법으로 pipenv를 설치할 수 있다.
> pypi.org-pipenv: https://pypi.org/project/pipenv/  
> pypi.org 사이트를 통하여 pipenv패키지를 다운로드 받고, `pip` 커맨드를 통하여 설치한다. 

```shell
# move downloaded pipenv package to pypi-server repo dir
mv <PIPENV_PACKAGE> <PYPI_SERVER_REPO_DIR>

# Install pipenv with pip
pip3 install [--user] pipenv

# --user 옵션은 현재 사용자의 권한으로 패키지를 설치하는 옵션.  
# 예를들어 기본적인 시스템 파이썬은 /usr/bin, /usr/local/bin,  등에 설치되어 있는 경우가 많고,  
# 일반 사용자가 쓰기 권한이 없는 경로일 가능성이 높다.  
# 또한 다른 유저가 본인의 경로에 설치한 파이썬의 경우에도 동일하게 패키지를 설치할 권한이 없기 때문에  
# 오류가 발생할 수 있다. 이러한 오류를 해결해주는 것이 --user 옵션이다. 
# 생략하여도 괜찮으며, 권한 오류가 발생할 시 사용해보자.
```
> pipenv 패키지 설치를 진행하면서 의존성 오류가 발생할 수도 있다.   
만약 의존성 오류가 발생한다면 관련 의존 패키지도 모두 다운로드 받아서 pypi-server repo directory에 넣어준다.  
그러면 pypi-server에 의하여 pip가 자동으로 관련 모든 패키지를 한번에 설치해줄 것이다. 

```shell
# Check Installation
which pipenv  # should return: <PYTHON_INSTALLATION_PATH>/bin/pipenv
```

#### 3. Use of pipenv
pipenv 설치까지 완료 되었다면 활용을 진행해본다.  
프로젝트 디렉토리를 생성하고, 해당 디렉토리 하위에서 가상 환경을 생성해본다. 
```shell
mkdir -p $HOME/development/my_project
cd $HOME/development/my_project
pipenv shell
 
# pipenv shell 커맨드는 현재 내 환경에 설정된 Python,
# (which python3 를 실행했을 때 나오는 경로에 위치한 Python)을 기준으로 하여 가상 환경을 설정한다.
# 만약 별도의 Python을 기준으로 잡고 싶다면 아래와 같이 사용할 수 있다.
# pipenv install --python <PYTHON_VERSION>
# 예) pipenv install --python 3.9.13
```
> `pipenv shell` 커맨드로 가상환경을 실행하였다면 가상환경 생성 및 가상환경 실행이 동시에 이루어 지게 된다.   
`pipenv install --python 3.9.13` 과 같이 `install` 커맨드를 사용하였다면 가상환경 생성만 완료되었을 뿐, 실행은 되지 않는다.  
이 경우 다시 `pipenv shell` 커맨드를 활용하여 생성된 가상환경을 실행하여 가상환경으로 진입 할 수 있다.  

위와 같이 설정된 가상환경은 이전에 시스템에 직접 설치한 Python과는 독립적인 화경을 받게된다.  
이후 가상환경 내에서 설치되는 모든 패키지는 해당 가상 환경에만 귀속되며, 다른 환경으로부터 영향을 받지도 않으며 영향을 끼치지도 않는다.  

생성한 Python가상환경을 살펴보자.  
Pipfile을 열여 확인해보면 어떤 source에서 패키지를 설치했는지, 현재 가상환경의 파이썬 버전은 어떤 버전인지 등의 정보가 나온다.  

해당 가상환경에서 `pipenv install <PACKAGE_NAME>`을 입력하여 패키지를 설치해보자.  
독립적인 가상환경에 패키지가 설치되며, 가상환경 외부로는 영향을 주지 않는다.   
또한 Pipfile.lock (lock file) 이 생성되며 Hash정보가 저장되며, Pipfile이 자동으로 업데이트 되는것을 확인해볼 수 있다.  
Pipfile은 직접 수정하여 작성하고 업데이트 할 수 있지만, Pipfile.lock파일은 절대로 직접 수정하여서는 안된다.  

현재 실행중인 가상환경을 나가기 위해서는 `exit` 을 입력하면 된다.  
생성된 가상환경을 제거하기 위해서는 Pipfile이 위치해있는 프로젝트 디렉토리에서 `pipenv --rm`을 입력하면 된다.

#### 4. Environment Variable
pipenv로 가상환경을 실행하게되면 해당 가상환경은 default로 설정된 경로에서 생성된다.  
보통 개인 홈 디렉토리 하위의 `~/.local/share/virtualenvs` 또는 `~/.local/share/.venv` 등의 경로로 생성되게 된다.  
하지만 해당 경로가 아닌 각 프로젝트 디렉토리에 가상환경 디렉토리를 바로 생성하고 싶다면 아래와 같은 환경변수(PIPENV_VENV_IN_PROJECT)를 등록해주면 된다.  
일회성으로는 `setenv` 커맨드를 사용할 수 있지만 영구적으로 설정하기 위해서는 .cshrc 파일에 등록해주어야 한다. 

```shell
# .cshrc
setenv PIPENV_VENV_IN_PROJECT 1
``` 

위 환경변수 등록 후 가상환경을 다시 만들어주자.  
이 후 `ls -la` 커맨드로 확인해보면 해당 프로젝트 디렉토리 하위에 `.venv` 디렉토리가 생긴것을 확인할 수 있다. 


#### 5. Install Packages within pipenv
지금까지 한것과 동일한 방법으로 Pandas 라이브러리를 가상환경에 설치해보자.  
아래와 같은 순서로 진행된다. 
- pypi.org 사이트에서 pandas 및 관련 의존 패키지를 모두 다운로드받아 pypi-server의 repo directory로 이동
- `pipenv shell` 또는 `pipenv install --python 3.9.13` 커맨드로 가상환경 생성 및 활성화 
  - 활성화 후 which python3를 입력하면 가상환경 디렉토리 (.venv 또는 virtualenvs)디렉토리 하위에 위치한 Python이 출력될것이다. 
- `pipenv install pandas`커맨드로 가상환경 내 패키지 설치

***
