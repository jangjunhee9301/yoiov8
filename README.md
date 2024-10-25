###### yolo 가상환경 만들기
``` bash
uname -a
wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh
````

#### 용어정리 

``` bash
 conda : 파이썬과 라이브러리들을 관리하고 설치할 수 있는 도구로, 가상 환경을 만들어 서로 다른 프로젝트의 패키지 버전을 분리해 관리할 수 있게 해줘요. YOLO 설치 시 필요한 라이브러리들도 쉽게 설치하고 충돌 없이 사용할 수 있습니다.


 archiconda :  Arch Linux에서 Conda를 쉽게 설치하고 사용할 수 있게 해주는 버전이에요. Conda로 파이썬 환경을 설정하고 패키지 관리를 할 수 있게 도와줘요.


 wget : 터미널에서 파일을 인터넷에서 다운로드할 때 쓰는 명령어예요.


  sh : 쉘 스크립트 파일을 실행할 때 쓰는 명령어예요.
```

##### 결과

  Archiconda3-0.2.3-Linux-aarch64.sh Pictures Desktop Public Documents Templates Downloads Videos examples.desktop yolov8_4gb Music

     ./Archiconda3-0.2.3-Linux-aarch64.sh
실행 중 선택이라 뜨면
yes---> enter ---> yes in your /home/ldh/.bashrc ? [yes|no] [no] >>> yes
이렇게 한다.

    conda env list
    conda activate base
    jetson_release 

    
### python 3.8 가상환경 만들기
***
base가 아닌 native에서 실행

    conda deactivate
 - 가상환경에서 빠져 나오는 명령어임
   
 ```
conda create -n yolo python=3.8 -y
```
이걸 입력하고 사진처럼 나온다면 조금 기다리면 된다.
![동아리](https://github.com/user-attachments/assets/80fd8a79-fc4a-4c49-85e0-48595e8c419d)

```
conda env list
conda activate yolo
 ```

 - "conda activate yolo"를 실행하여 yolo 가상환경으로 진입해서 pytorch, torchvosion을 설치하는 과정이다.
 - 결과 가상에서 설치 torch, torvosion 다운로드
 - torch은 과학 계산과 머신러닝 알고리즘을 지원하는 프레임워크이며, 주로 PyTorch로 알려진 딥러닝 라이브러리에서 사용됩니다.
 - Torchvosion은 PyTorch에서 컴퓨터 비전 작업을 쉽게 하기 위한 라이브러리로, 이미지 처리용 데이터셋, 모델, 전처리 도구를 제공합니다.

(yolo) dli@dli:~$
```
pip install -U pip wheel gdown
```
```
gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM
```

```
gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV
```

아래 두 라인을 실행(library 설치) 후 torch, torchvision은 확인이 가능하였다.

```
sudo apt-get install libopenblas-base libopenmpi-dev
sudo apt-get install libomp-dev
pip install torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl
python -c "import torch; print(torch.__version__)"
```
```
(yolo) dli@dli:~$ python

>>> import torch
>>> import torchvision
>>> print(torch.__version__)
>>> print(torchvision.__version__)
>>> print("cuda used", torch.cuda.is_available())
cuda used True
>>> 
```
***
```
(yolo) dli@dli-desktop:~$ python
Python 3.8.13 | packaged by conda-forge | (default, Mar 25 2022, 05:56:18) 
[GCC 10.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
 >>> import torch
 >>> import torchvision
 >>> print(torch.__version__)
1.11.0a0+gitbc2c6ed
 >>> print(torchvision.__version__)
0.12.0a0+9b5a3fe
 >>> print("cuda used", torch.cuda.is_available())
cuda used True
 >>> 
```
***
이렇게 떠야한다.
위에서 true가 뜨면 ctrl + d 를 눌러서 탈출한다.

```
git clone https://github.com/Tory-Hwang/Jetson-Nano2
```
```
(yolo) dli@dli:~$ cd Jetson-Nano2/
(yolo) dli@dli:~/Jetson-Nano2$ cd V8
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install ultralytics
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install -r requirements.txt 
(yolo) dli@jdli:~/Jetson-Nano2/V8$ pip install ffmpeg-python
(yolo) dli@dli:~/Jetson-Nano2$ sudo apt install tree
(yolo) dli@jdli:~/Jetson-Nano2$ tree -L 2
```
 - 여기서 cd는 파일을 변경하는 명령어다.
 - 이 위에꺼는 굳이 안해도 된다.
 - 다 했으면 https://github.com/ultralytics/ultralytics?tab=readme-ov-file 이 링크에서
YOLOv8n을 다운 받는다. 그리고 그 파일의 경로만 알아두면 된다.
1. 내 컴퓨터
2. Jetson-nano2
3. V8
4. detectY8.py
5. brtsp = True 라고 되어있는 것을 brtsp = False로 바꾼다.

이제 v8 파일로 가서
```
python3 detectY8.py
```
이렇게 하면 카메라가 화면에 뜬다


