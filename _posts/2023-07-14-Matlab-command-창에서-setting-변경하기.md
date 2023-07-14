---
layout: post
title: Matlab command 창에서 setting 변경하기
date: 2023-07-14 09:26 +0900
author:
image:
categories:
tags: [matlab]
---

matlab 라이브편집기에서 latex로 내보내기를 하면 기본적으로 이미지가 eps 포멧으로 저장된다.

이미지를 png 형식으로 출력되도록 하려고 ui에서 세팅을 찾아도 찾을수가 없었다.

이때 command 창에서 아래와 같이 바꿀 수 있다.

기타 다른 속성들도 아래와 같이 바꿀수 있겠다.

[matlab.editor 설정](https://kr.mathworks.com/help/matlab/ref/matlab.editor-settings.html#responsive_offcanvas)

```matlab
s = settings;
s.matlab.editor.export.latex.FigureFormat.PersonalValue = 'png'

>> s.matlab.editor.export.latex.FigureFormat

ans =

  Setting 'matlab.editor.export.latex.FigureFormat' - 속성 있음:

          ActiveValue: 'png'
       TemporaryValue: <no value>
        PersonalValue: 'png'
    InstallationValue: <no value>
         FactoryValue: 'eps'

```

추가적으로 [livescript2markdown](https://github.com/minoue-xx/livescript2markdown)을 이용하면 이를 다시 markdown 형식으로 바꿀 수도 있다.