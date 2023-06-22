---
layout: post
title: Anaconda Update 방법
date: 2023-06-22 16:52 +0900
author: jeongcho
image:
categories:
tags: [python]
---

python 배포판인 anaconda를 update 하는 방법이다.

1. 관리자 권한으로 Anaconda prompt를 실행한다.

    ![input_img1](assets/img/2023-06-22_16_41_21.png)

2. conda package를 update 한다.

    > `conda update -n base conda`

3. 현재 선택된 가상 환경의 모든 package를 update 한다.

    > `conda update --all`

4. pip 를 upgrade 한다.

    > `python.exe -m pip install --upgrade pip`

    이때 에러가 발생할 경우 <a href="https://bootstrap.pypa.io/get-pip.py" target="_blank">https://bootstrap.pypa.io/get-pip.py</a> 링크로 이동하여 get-pip.py 파일을 다운로드 한 후 아래 명령으로 수동 설치한다.

    > `python.exe get-pip.py`