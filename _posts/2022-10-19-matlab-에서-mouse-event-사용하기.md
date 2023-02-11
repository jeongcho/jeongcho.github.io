---
layout: post
title: Matlab 에서 mouse event 사용하기
date: 2022-10-19 09:48 +0900
author:
image:
categories:
tags: matlab
---


Matlab 에서 특정 data를 plot 한 후에 간단하게 mouse event를 활용하고 싶을 때가 있습니다.

아래 예제와 같은 형식으로 간단하게 활용 가능합니다.

```matlab

F=figure(1);
clf
set(F,'Position',[100 600 600 400]);

a1 = axes();
a2 = axes();
set(a1,'Position',[0.1 0.6 0.8 0.35])
set(a2,'Position',[0.1 0.15 0.8 0.35])
p2 = plot(rand(1,1024));
axis([0 1024 0 1]);

set(a1,'ButtonDownFcn', {@lineCallback,p2})
set(F,'WindowButtonMotionFcn', {@lineCallback,p2,a1})

function lineCallback(src,event,p,a)
	disp(src);
	disp(event);
	if gca()==a
   	set(p,'Ydata',rand(1,1024));
		point = get(a,'CurrentPoint');
		disp(point(1,:))
	end
end

```

a1 창에서 마우스 클릭하여 active 한 후에
마우스 포인터가 이동할 때마다 event 가 발생한다.

![Desktop View](assets/img/202210191001.PNG)

