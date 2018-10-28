## LeeYeJin

2017261038 이예진 과제 
===========
*****

1.깃 명령어
-------------

### 1) 기본 명령어
저장소 생성 
<pre><code> git init </code></pre>
원격 저장소로부터 복제 
<pre><code> git clone {url}</code></pre>
변경 사항 체크
<pre><code> git status // </code></pre>
특정 파일 스테이징
<pre><code> git add {파일 이름} </code></pre>
변경된 모든 파일 스테이징 
<pre><code> git add * </code></pre>
원격으로 보내기
<pre><code> git push origin master </code></pre>
원격 저장소 추가
<pre><code> git remote add origin {원격서버주소} </code></pre>

### 2) Commit
커밋 (변경을 기록) 
<pre><code> git commit -m “{변경 내용}” </code></pre>
커밋 합치기 
<pre><code> git rebase -i HEAD~4 // 최신 4개의 커밋을 하나로 합치기</code></pre>
커밋메세지 수정
<pre><code> $ git commit --amend // 마지막 커밋메세지 수정(ref)</code></pre>
간단한 commit방법
<pre><code>$ git add {변경한 파일명}
$ git commit -m “{변경 내용}"</code></pre>
커밋 이력 확인
<pre><code>$ git log // 모든 커밋로그 확인
$ git log -3 // 최근 3개 커밋로그 확인
$ git log --pretty=oneline // 각 커밋을 한 줄로 표시</code></pre>
커밋 취소
<pre><code>$ git reset HEAD^ // 마지막 커밋 삭제
$ git reset --hard HEAD // 마지막 커밋 상태로 되돌림
$ git reset HEAD * // 스테이징을 언스테이징으로 변경, ref </code></pre>

### 3) Branch
master 브랜치를 특정 커밋으로 옮기기
<pre><code>git checkout better_branch
git merge --strategy=ours master    # keep the content of this branch, but record a merge
git checkout master
git merge better_branch            # fast-forward master up to the merge</code></pre>
브랜치 목록
<pre><code>$ git branch // 로컬
$ git branch -r // 리모트 
$ git branch -a // 로컬, 리모트 포함된 모든 브랜치 보기 </code></pre>
브랜치 생성
<pre><code>git branch new master // master -> new 브랜치 생성
git push origin new // new 브랜치를 리모트로 보내기</code></pre>
브랜치 삭제
<pre><code>git branch -D {삭제할 브랜치 명} // local
git push origin :{the_remote_branch} // remote </code></pre>
빈 브랜치 생성
<pre><code>$ git checkout --orphan {새로운 브랜치 명}
$ git commit -a // 커밋해야 새로운 브랜치 생성됨
$ git checkout -b new-branch // 브랜치 생성과 동시에 체크아웃 </code></pre>
리모트 브랜치 가져오기
<pre><code>$ git checkout -t origin/{가져올 브랜치명} // ref </code></pre>
브랜치 이름 변경
<pre><code>  $ git branch -m {new name} // ref</code></pre>

### 4) Tag
태그 생성
<pre><code>git tag -a {tag name} -m {tag message} {commit hash}
git tag {tag name} {tag name} -f -m "{new message}" // Edit tag message </code></pre>
태그 삭제
<pre><code>git tag -d {tag name}
git push origin :tags/{tag name} // remote</code></pre>
태그 푸시
<pre><code>git push origin --tags
git push origin {tag name}
git push --tags</code></pre>

### 5) 서버설정
강제 푸시 설정
<pre><code>git config receive.denynonfastforwards false </code></pre>

### 6) Alias
~/.gitconfig 파일을 설정하여 깃 명령어의 앨리어스를 지정할 수 있다.

~/.gitconfig > alias 부분:
<pre><code> [alias]
  br = branch
  co = checkout
  rb = rebase
  st = status
  cm = commit
  pl = pull
  ps = push
  lg = log --graph --abbrev-commit --decorate --format=format:'%C(cyan)%h%C(reset) - %C(green)(%ar)%C(reset)  %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(yellow)%d%C(reset)' --all
  ad = add
  tg = tag
  df = diff </code></pre>
  
### 7) 그 외
파일 삭제
<pre><code> git rm --cached --ignore-unmatch [삭제할 파일명] </code></pre>
히스토리 삭제
<pre><code>$ git clone [url] # 소스 다운로드
$ cd [foler_name] # 해당 폴더 이동
$ git filter-branch --index-filter 'git rm --cached --ignore-unmatch [삭제할 파일명]' --prune-empty -- --all 
# 모든 히스토리에서 해당 파일 삭제
$ git push origin master --force # 서버로 전송 </code></pre>
히스토리에서 폴더 삭제:
<pre><code>git filter-branch --tree-filter 'rm -rf vendor/gems' HEAD</code></pre>
리모트 주소 추가하여 로컬에 싱크하기
<pre><code>$ git remote add upstream {리모트 주소}
$ git pull upstream {브랜치명}</code></pre>
최적화
<pre><code>$ git gc
$ git gc --aggressive</code></pre>  
  

2.마크다운 문법
----------
### 1) 마크다운이란? 
마크다운(markdown)은 텍스트 기반의 마크업 언어로, 2004년 존 그루버에 의해 만들어졌다. 
README 파일이나 온라인 문서, 혹은 일반 텍스트 편집기로 문서 양식을 편집할 때 쓰인다. 
마크다운을 이용해 작성된 문서는 쉽게 HTML 등 다른 문서형태로 변환이 가능하다.

### 2) 마크다운 문법
#### 1 - 헤더
* 큰 제목 : 문서 제목
<pre><code>This is an H1
=============</code></pre>
This is a H1
=============
* 작은 제목 : 문서 부 제목
<pre><code>This is an H2
------------</code></pre>
This is a H2
-------------- 
* 글머리 : #~######까지만 지원
<pre><code># This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6 </code></pre>
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6 

#### 2 -  BlockQuote

이메일에서 사용하는 > 블럭인용문자를 이용한다.
<pre><code>>This is a blockqute. 
>> This is a blockqute.
>>> This is a blockqute.</code></pre>
> This is a blockqute.
>> This is a blockqute.
>>> This is a blockqute.

#### 3 -  목록
* 순서 있는 목록(번호)
<pre><code>1. 첫번째
2. 두번째
3. 세번째</code></pre>
1. 첫번째
2. 두번째
3. 세번째

어떠한 번호를 입력해도 순서는 내림차순으로 정의된다.
* 순서 없는 목록(글머리 기호)
<pre><code>* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑</code></pre>
* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑

혼합해서 사용하는것도 가능   

#### 4 -  코드<pre><code></code></pre>
<pre><code> This is a code block. </code></pre>

#### 5 -  수평선
<pre><code>* * *

***

*****

- - -

---------------------------------------
</code></pre>
* * *

***

*****

- - -

---------------------------------------
#### 6 -  링크
* 참조링크
<pre><code>[link keyword][id]
[id]: URL "Optional Title here"

Link: [Google][googlelink]
[googlelink]: https://google.com "Go google" </code></pre>
[link keyword][id]
[id]: URL "Optional Title here"

Link: [Google][googlelink]
[googlelink]: https://google.com "Go google"
* 인라인  링크
<pre><code>syntax: [Title](link) </code></pre>
syntax: [Title](link)

### 7 - 강조

<pre><code>*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
++underline++
~~cancelline~~ </code></pre>
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
++underline++
~~cancelline~~

### 8 - 이미지
<pre><code>![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")</code></pre>
사이즈 조절은 <pre><code><img width="" height=""></img> </code></pre>를 이용한다.
