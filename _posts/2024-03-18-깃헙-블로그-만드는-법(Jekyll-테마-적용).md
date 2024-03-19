---
layout: post
title: Jekyll 테마를 적용한 Github 블로그 만드는 법 (Windows 기준)
tags: [깃허브 블로그, github 블로그, jekyll 테마, jekyll]
toc:  true
---

바로 시작해봅시다! 
공식 문서로 정리가 이미 잘 되어 있으니 여길 참고하셔도 좋습니다. 
<a href="https://pages.github.com/">https://pages.github.com/</a>

## 1. 저장소(repository) 생성하기<br/>

우선 Github 블로그인만큼 계정이 있어야겠죠? 아직 계정이 없다면 회원가입과 git 설치까지 완료하고 진행하시길 바랍니다. 자, 계정이 있다면 [Github](https://github.com/)에 로그인을 합니다. 우측 상단의 Sign in이 로그인입니다.  
![github page](/assets/img/githubPage.png "Github 홈페이지")<br/>

로그인 후 좌측의 New 초록 버튼을 누르거나 우측 상단 +의 new repository를 눌러  블로그 파일을 저장할 저장소를 생성해줍니다.  
![github rep](/assets/img/create rep1.png)
![github rep](/assets/img//create rep2.png)<br/>

Repository name에는 <mark>username.github.io</mark>을 작성해야 합니다. 이 때, username에는 Owner에 적혀있는 본인의 이름을 작성해야 합니다. 제 경우에는 LYJ22.github.io인거죠. 이름이 곧 주소가 되기 때문에 "나는 이 아이디로 된 주소 만들기 싫은데...🤔" 하면서 다른 이름을 쓰면 안된다고 합니다. 그 아래는 건드릴 필요 없이 바로 create repository 버튼을 눌러서 계속 진행하셔도 됩니다.  
![github rep](/assets/img/create rep3.png)

## 2. Jekyll 설치<br/>

저는 Windows11 환경을 사용하기 때문에 윈도우 사용자 기준에서 작성했습니다. Jekyll 테마를 적용하기 앞서 우선 루비를 설치해야 합니다. <a href="https://rubyinstaller.org/downloads/">루비 다운로드</a>  
몇 개의 블로그를 구경해보니 맥 사용자이신 분들은 루비를 설치하지 않아도 되는 것 같더라고요. 하지만 이 글을 읽는 우리는 윈도우 사용자니까~ 다운로드 해주세요! 작성하고 있는 지금은 Ruby+Devkit 3.2.3-1 버전입니다. With devkit 중 제일 높은 버전을 다운로드 받아 설치 진행하시면 됩니다.  
![github rep](/assets/img/dwl ruby.png)<br/>

설치가 끝난 후 터미널에 <mark>ruby --version</mark> 커맨드를 입력했을 때 다운로드한 버전이 출력되는 걸로 정상적으로 설치가 됐는지 확인할 수 있습니다. 잘 설치가 됐다면 아래의 2가지 명령어를 입력해 설치를 마저 해줍니다.
```
gem install bundler
gem install jekyll
```
<br/>
Jekyll 사이트가 잘 생성되는지 확인해볼까요? 파일 탐색기를 열어 원하는 위치에 폴더를 하나 만들어줍니다. 이 폴더에 본인이 만든 username.github.io 저장소를 clone해주세요. README.md 파일이 있다면 지워서 빈 폴더인 상태로 아래의 명령어를 입력해줍니다.
```
jekyll new .
```
git에서 명령어를 입력해서 안되면 터미널에서 해당 폴더 위치로 이동한 다음에 입력하면 되실겁니다. 폴더에 파일이 몇 개 생성이 되었다면 아래 명령어로 로컬 서버 실행을 해보세요.
```
bundle exec jekyll serve
```
제대로 실행된다면 server address가 뜰 것이고 해당 주소로 접속하면 Welcome to Jekyll!이라는 문구가 보입니다. 만약 문제가 생기면 <mark>bundle add webrick</mark> 명령어를 입력한 뒤에 다시 시도해보세요.

## 3. Jekyll 테마 적용하기  

이제 테마를 찾아볼 시간입니다. 구글에 jekyll theme을 검색하면 몇 개의 사이트가 나오는데 거기서 마음에 드는 디자인을 고르시면 됩니다. 종류가 워낙 많아서 저는 괜찮아보이는 게 눈에 들어오자마자 바로 선택했습니다😵. 사이트에서 원하는 디자인을 고르셨으면 해당 테마의 파일을 github에서 다운로드 합니다. download zip을 사용하는 게 편합니다.
![github rep](/assets/img/dwl theme.png)<br/>

zip 파일을 압축 해제해서 나온 모든 파일을 전부 복사합니다. 그리고 아까 jekyll을 설치했던 폴더에 붙여넣습니다. 중복 경고가 뜨면 모두 덮어쓰기 하시면 됩니다. 그리고 첫 번째 중요한 점! **Gemfile.lock 파일을 삭제해줍니다.** 버전 차이 때문인지 jekyll 사이트가 제대로 생성되지 않아 한참을 검색했습니다😅. 폴더 위치에서 아래 명령어를 실행하면 다시 Gemfile.lock 파일이 생성됩니다.
```
bundle install
```
<br/>
두 번째 중요한 점은 config.yml 파일입니다. 해당 파일에서 몇 가지 블로그 설정을 할 수 있으니 찾아서 열어주세요. 기본적으로 title은 블로그 이름, description은 블로그 설명에 해당합니다. 지금 보고 계시는 이 블로그의 title은 "YJ의 저장소"이고 description은 "이것저것 기록합니다"인거죠. 그 외 설정법이 다양하게 있지만 저도 이제 막 시작한 터라 나중에 좀 더 능숙해지면 아래 추가하거나 따로 정리해서 올려보겠습니다.<br/>

설정을 마치셨으면 아래 명령어를 입력해 다시 한 번 서버 주소로 접속해보세요.
```
bundle exec jekyll serve
```
   
그러면 짜잔~! 블로그가 드디어 만들어졌습니다~

## 4. Github에 업로드  
이제 파일을 업로드합니다. git에서 아래 명령어를 순서대로 입력해주세요.
```
git add .
git status
git commit -m "first commit"  //원하는 메시지로 변경 가능
git push
```
<br/>

push가 잘 됐으면 github에 파일이 업로드 된 것을 볼 수 있습니다.
![github rep](/assets/img/blogGithub1.png)
<br/>

메뉴에서 Settings -> Pages로 들어가보시면 Visit site 버튼을 찾을 수 있습니다.
![github rep](/assets/img/blogGithub2.png)
<br/>

이렇게 github 블로그 생성이 끝났네요. 이제 파일을 열어보면서 원하는 대로 블로그를 개조(?)해가면 됩니다. 저도 마저 인테리어 하러 갑니다...