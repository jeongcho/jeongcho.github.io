---
layout: post
title: Vivado simulation error [common 17-162] 발생할 경우
date: 2024-02-15 10:30 +0900
author: 
image:
categories:
tags: [fpga,vivado]
---

vivado IDE project 환경에서 갑자기 아래와 같은 데러가 발생하며 simulation 이 안될때가 있다.

```vivado [common 17-162] invalid option value specified for '-files'.```

이때는 사용중인 모든 IP의 Core Container 설정을 disable 하면 error 가 해결 된다.

![image](assets/img/fpga/2024-02-15_10_33_23.png)

[링크 참조](https://support.xilinx.com/s/question/0D52E00006hprwZSAQ/error-when-trying-to-run-simulation-after-upgrading-to-20211?language=en_US)
