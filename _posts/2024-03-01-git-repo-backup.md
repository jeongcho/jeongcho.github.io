---
layout: post
title: Github의 repositories를 Hdd에 백업하기
date: 2024-03-01 09:54 +0900
author: 
image:
categories:
tags: [python,git]
---

혹시나 하는 마음에 github의 repositories를 가끔씩 하드디스크에 백업하고 싶을때가 있다.

이때는 아래와 같이 github의 API를 이용해서 repositories 목록을 가져오고 자동으로 진행되도록 처리 할 수 있다.

github token은 settings -> Develpoer settings -> Tokens 에서 만들 수 있다.

![image](assets/img/2024-03-01_09_59_08.png)

![image](assets/img/2024-03-01_09_59_25.png)

![image](assets/img/2024-03-01_09_59_38.png)

```python
import requests
import subprocess
import os

# 사용자 설정
GITHUB_USER = '% 사용자이름 %'
ACCESS_TOKEN = '% github token %'
DEST_FOLDER = 'D:\\backup'

url = 'https://api.github.com/user/repos?per_page=100&type=all'
headers = {'Authorization': f'token {ACCESS_TOKEN}'}
response = requests.get(url, headers=headers)

# 응답 확인
if response.status_code == 200:
    repositories = response.json()
    n=1
    for repo in repositories:
        clone_url = repo['clone_url']
        repo_name = repo['name']
        dest_path = os.path.join(DEST_FOLDER, repo_name)

        # # 리포지토리 클론
        # print(f'{n} : Cloning {repo_name}...')
        # subprocess.run(['git', 'clone', clone_url, dest_path])

        # 해당 폴더가 이미 존재하는 경우, git pull 실행
        if os.path.isdir(dest_path):
            print(f'{n} : Updating {repo_name}...')
            subprocess.run(['git', '-C', dest_path, 'pull'])
        else:
            # 폴더가 존재하지 않는 경우, 새로 클론
            clone_url = repo['clone_url']
            print(f'{n} : Cloning {repo_name}...')
            subprocess.run(['git', 'clone', clone_url, dest_path])

        n=n+1
    print('All repositories have been cloned.')
else:
    print('Failed to retrieve repositories. Please check your settings.')
```
