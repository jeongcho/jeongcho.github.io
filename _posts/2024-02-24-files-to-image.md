---
layout: post
title: 여러장의 작은 이미지를 모아서 보고싶을때 markdown 파일 자동으로 만들기
date: 2024-02-24 11:27 +0900
author: 
image:
categories:
tags: [python,music]
---

여러장의 작은 이미지를 모아서 보고싶을때 markdown 파일을 자동으로 만들어 주면 편하다.

```python
import os

def create_image_list_file(directory, height):
    files = os.listdir(directory)
    png_files = [file for file in files if file.lower().endswith('.png')]
    png_files.sort()
    content = '\n'.join(f'<img src="{file}" height="{height}">' for file in png_files)
    text_file = "image_list.md"
    text_file_path = os.path.join(directory, text_file)
    with open(text_file_path, 'w') as file:
        file.write(content)
    return text_file_path

directory = os.getcwd()
height = 120
text_file_created = create_image_list_file(directory, height)
```
