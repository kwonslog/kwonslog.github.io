---
published: false
layout: single
title: "나의 개발 도구"
excerpt: "사용하고 있는 개발 도구 목록을 관리"
date: 2025-08-23
last_modified_at: 2025-08-23
categories: [dev]
tags: [tool]
toc: true
---

## 에디터
- [Sublime Text](https://www.sublimetext.com/)
  - EditPlus 를 다음으로 선택한 에디터.
  - 변화가 필요한 시점이기도 해서 잘 사용하기 위해 적응중.
  - 설치한 패키지
    - 마크다운 문서를 위해 Markdown Editing, Markdown Preview, Side Bar, Table Editor 사용.
    - Terminus : 에디터 안에서 터미널 실행 가능.
      - Terminus 로 gemini cli 를 실행 했는데 `한글 입력이 안됨`. 대안으로 윈도우 터미널 창을 사용함.
        ```
        1. 상단 메뉴 → Preferences → Browse Packages…
        2. `User` 폴더 들어가기
        3. `Default.sublime-commands` 파일이 없다면 생성하고 아래 내용 추가
        
        [
            {
                "caption": "Windows Terminal : Open Gemini CLI",
                "command": "exec",
                "args": {
                    "shell_cmd": "start \"\" wt -p \"Command Prompt\" -d \"C:\\Kwon\\gemini-cli\" cmd /k gemini"
                }
            }
        ]
        ```
  
- [EditPlus](https://www.editplus.com/)
  - 개발자로 입문 했을때 부터 사용했던 에디터.
  - 사용하면서 크게 불편한 점은 없었다.

## IDE
- [Eclipse](https://www.eclipse.org/)
  - 웹 어플리케이션 개발을 본격적으로 시작하면서 주력으로 사용했던 도구.
  - 요즘은 사용하지 않은지 꽤 되었다.
 
- [Visual Studio Code](https://code.visualstudio.com/)
  - paython, Nodejs Nextjs, Nuxtjs 관련 개발 할때 현재 사용중인 도구.
 
- [IntelliJ](https://www.jetbrains.com/)
  - 최근 spring 개발할때 사용한 도구.
  - Eclipse -> Visual Studio Code -> IntelliJ 순서로 사용했었던 도구.
 
## 마크다운
- [MarkText](https://github.com/marktext/marktext)
  - 윈도우용으로 사용할 마크다운 뷰어를 찾다가 알게됨.
  - 편집과 미리보기가 합쳐져 있는데 좀 불편한 부분이 있어서 Sublime Text 로 넘어가기로 함.
  
    
