## **git flow model**

**git flow : 브랜치를 어떻게 운영할 것인가에 대한 좋은 사례**

<br><p align="center"><img src="/git&github/img/1.png"></p><br>

#### **git flow model**

-   **master branch : 제품으로 출시될 수 있는 브랜치, 언제나 실행 가능한 상태를 유지하며 배포 이력을 관리.**
-   **develop branch : 다음 출시 버전을 개발하는 브랜치, 기능 개발을 위한 브랜치들을 병합하기 위해 사용.**
-   **feature branches : 기능 개발할 때 사용**
    1.  'develop' 브랜치에서 새로운 기능에 대한 feature 브랜치를 분기한다.
    2.  새로운 기능에 대한 작업을 수행한다.
    3.  작업이 끝나면 'develop' 브랜치로 병합(merge)한다.
    4.  더 이상 필요하지 않은 feature 브랜치는 삭제한다.
    5.  새로운 기능에 대한 'feature' 브랜치를 중앙 원격 저장소에 올린다.(push)
-   ****release braches : 출시할 때 사용****
-   ****hotfix branch : 긴급한 수정사항을 반영할 때 사용****

<br><br>

### **실습으로 알아보기**

```
$ git init
$ git add main.txt
$ git commit -m "work 1"
```

<br><p align="center"><img src="/git&github/img/2.png"></p><br><br><br>


#### **git tag**

-   지금까지 만들어왔던 프로그램, 완성된 프로그램을 출시를 최초로 했다고 하면 출시한 버전을 기록해야한다.
-   이때 사용하는 것이 **git tag**.

```
$ git tag 0.1
```

<br><p align="center"><img src="/git&github/img/3.png"></p><br><br><br>

#### **master branch**

<br>

-   이제 계속해서 기능 개선이나 새 기능을 추가, 버그 수정을 해야하는데, master branch에서 하지않는다.
-   master는 언제나 실행가능한 상태를 유지해야 한다.
-   즉, master의 가장 최신 버전은 언제나 실행 가능해야한다.
-   실행가능한 과정을 만들어가는 과정은 develop branch에서 진행한다.

<br><br>

#### **develop branch**

<br>

\- develop branch만들어서 이동

```
$ git checkout -b develop
```

<br>

\- 버그를 개선한다.

```
# main.txt

1
2 (버그 수정)
```

<br>

\- git commit -am "message" 

> git commit -a : 스테이징 절차(add)를 생략하고 바로 add+commit

```
$ git commit -am "work 2"

```

<br><p align="center"><img src="/git&github/img/4.png"></p><br>

<br>

\- 추가 기능 개선

```
# main.txt

1
2 (버그 수정)
3 (기능 개선)
```
<br>

\- git commit -am "message" 

```
$ git commit -am "work 3"

```

<br><p align="center"><img src="/git&github/img/5.png"></p><br>

이런식으로 develop에서 작업을 진행한다.

기능개선이 끝나고 버그를 수정했다.

그 다음은 출시 준비를 해야한다.

이때 사용하는 브랜치가 **release branch**

<br><br>

#### ****release branch****

```
$ git checkout -b release/0.2
```

-   현재 출시된 버전은 0.1
-   0.1에서 기능개선/버그수정이 develop 브랜치에서 이루어짐
-   0.2 브랜치를 출시할 준비를 하겠다는 의미로 release/0.2를 생성

<br>

자, 이렇게 **0.2 출시를 하려고 준비 했는데** 보니까 빨리 수정해야할 버그가 있다고 가정해보자.

그러면 버그 픽스를 해야한다.

release를 위한 버그 픽스는 'release-02.txt'라고하는 파일에서 진행해보자.

<br>

\- 버그 수정

```
# release-02.txt
1 (버그 수정)
```

<br>

\- 커밋

```
$ git add release-02.txt
$ git commit -am "release 0.2 1"
```

<br>

\- 추가 버그 수정

```
# release-02.txt
1 (버그 수정)
2 (버그 수정)
```

<br>

\- 커밋

```
$ git commit -am "release 0.2 2"
```

<br><p align="center"><img src="/git&github/img/6.png"></p><br>

<br><br>

#### **release ↔ develop**

<br>

**relaese 0.2 1** 과 **relaese 0.2 1** 는 나중에 develop branch에 병합되어야 한다.

> 그림 상에서도 release에서 develop으로 계속 병합 작업을 해주면서  
> 나중에 develop에서 발생할 충돌을 최소화 시킨다.

<br><p align="center"><img src="/git&github/img/7.png"></p><br>

<br>

\- 브랜치 이동

```
$ git checkout develop
```
<br>

\- 병합

```
$ git merge release/0.2
```

<br><p align="center"><img src="/git&github/img/8.png"></p><br>

<br><p align="center"><img src="/git&github/img/9.png"></p><br>

<br><p align="center"><img src="/git&github/img/10.png"></p><br>

<br>
이렇게 release에서 작업을 하고 develop으로 병합하는 작업을 반복하면서 release 준비가 끝난다.

```
$ git checkout release/0.2
```

<br>

#### **release↔ master**

<br><p align="center"><img src="/git&github/img/11.png"></p><br>

> 그림처럼 이제 잘 작동하는 걸 최종적으로 확인했다고 master branch에 병합한다.  
> 일반적인 병합을 사용하지 않고 merge commit을 남기는 형식의 병합을 사용한다.

<br>

\- 브랜치 이동

```
$ git checkout master
```

<br><br>

**git merge --no-ff**

> git merge release/0.2 명령어를 사용하면  
> release/0.2가 있는 커밋으로 fast forward 하기 때문에 병합이 어떻게 이루어졌는지 기록이 남지 않는다.  
> git merge --no-ff release/0.2  (no fast forward)라는 뜻

```
$ git merge --no-ff release/0.2
```

<br>
release/0.2와 병합했다 라는 commit message를 의도적으로 만들면서 log상의 기록을 남겼다.

<br><p align="center"><img src="/git&github/img/12.png"></p><br>
<br><p align="center"><img src="/git&github/img/13.png"></p><br>


> master가 release/0.2를 따라왔다.  
> 이렇게 하는 이유는 브랜치가 너무 많아지는 것을 방지.

<br>

\- release/0.2 브랜치 삭제 (기록은 남아있음)

```
$ git branch -d release/0.2
```

<br><p align="center"><img src="/git&github/img/14.png"></p><br>
<br><p align="center"><img src="/git&github/img/15.png"></p><br>

<br>

\- 이 제품을 출시할 때 버전을 기록하기 위해 태그

```
$ git tag 0.2
```

<br><p align="center"><img src="/git&github/img/16.png"></p><br>
<br><p align="center"><img src="/git&github/img/17.png"></p><br>

0.2 버전 출시 완료.

<br><br>

#### **다시 개발 시작**

<br>

\- 브랜치 이동

```
$ git checkout develop
```

-   신규로 추가할 기능 2개가 있다고 가정한다.
-   하나는, 금방 끝나고 ('short'라는 기능)
-   다른 하나는 오래걸린다고 가정하자. ('long'이라는 기능이라고 하자)

<br>

\- 신규 기능을 위한 branch를 만든다.

```
$ git branch feature/short
$ git branch feature/long
```

<br>

\- 브랜치 변경

```
$ git checkout feature/short
```

<br>

\- 기능 추가

```
# short.txt
1 (기능 추가)
```

<br>

\- 커밋

```
$ git add short.txt
```

```
$ git commit -am "short 1"
```

<br><p align="center"><img src="/git&github/img/18.png"></p><br>

<br>

\- 기능 추가

```
# short.txt
1 (기능 추가)
2 (기능 추가)
```

<br>

\- 커밋

```
$ git commit -am "short 2"
```

<br><p align="center"><img src="/git&github/img/19.png"></p><br>

**long 프로젝트도 병렬로 동시 진행한다.**

<br>

\- 세부 내용 생략

```
$ git checkout feature/long
```

.

.

```
$ git commit -am "long 2"
```

<br><p align="center"><img src="/git&github/img/20.png"></p><br>

<br><br>

**출시 준비를 해보자.**

<br>

\- 브랜치 이동과 병합

```
$ git checkout devlop
$ git merge --no-ff feature/short #이번엔 short만 담아서 출시
```

<br><p align="center"><img src="/git&github/img/21.png"></p><br>
<br><p align="center"><img src="/git&github/img/22.png"></p><br>

<br>

\- short 브랜치 삭제

```
$ git branch -d feature/short #삭제
```

<br><p align="center"><img src="/git&github/img/23.png"></p><br>

<br>

\- release 브랜치 생성과 변경

```
$ git checkout -b release/1.0
```

<br><p align="center"><img src="/git&github/img/24.png"></p><br>
<br><p align="center"><img src="/git&github/img/25.png"></p><br>

<br><br>

**release하면서 발생하는 자잘한 문제들이 있다고 가정하자.**

<br>

\- short.txt에 "3 (bug fix)" 추가 (세부 내용 생략)

<br>

\- 커밋

```
$ git commit -am "short 3 - bug fix"
```

<br><p align="center"><img src="/git&github/img/26.png"></p><br>

<br><br>

**기존의 작업에서도 문제가 발생할 수 있다.**

<br>

\- main.txt에 "4 (문제 개선)" 추가 (세부 내용 생략)

<br>

\- 커밋

```
$ git commit -am "work 4 - bug fix"
```

<br><p align="center"><img src="/git&github/img/27.png"></p><br>

이제 모든 작업을 마쳤다면 master로 보내고 develop에 머지해야한다.

<br><br>

**develop으로 병합작업**

<br>

\- develop 브랜치로의 이동과 병합

```
$ git checkout develop
$ git merge --no-ff release/1.0
```

<br><p align="center"><img src="/git&github/img/28.png"></p><br>

<br>

\- master 브랜치로의 이동과 병합

```
$ git checkout master
$ git merge --no-ff release/1.0
```

<br><p align="center"><img src="/git&github/img/29.png"></p><br>

<br>

\- 출시 버전 태그 달기

```
$ git tag 1.0
```

<br><p align="center"><img src="/git&github/img/30.png"></p><br>

<br>

\- release/1.0 브랜치 삭제

```
$ git branch -d release/1.0
```

<br><p align="center"><img src="/git&github/img/31.png"></p><br>

<br>

-   그런데 갑자기 긴급하게 수정해야 할 심각한 문제 발생했다고 가정하자.
-   근데 작업중인 'long'기능이 있다. ex) 2.0을 준비중인데 1.0이 운영중인 상황

<br>

이럴 때는 **hotfiexs branch**를 이용한다.

<br><br>

#### ****hotfiexs branch****

<br>

\- 브랜치 생성과 이동

```
$ git checkout -b hotfixes/1.1
```

<br><p align="center"><img src="/git&github/img/32.png"></p><br>

<br>

\- 문제 개선

```
# hotfix-1_1.txt
1 (문제 개선)
```

<br>

\- 커밋

```
$ git add hotfix-1_1.txt
$ git commit -am "hotfix 1.1"
```

<br><p align="center"><img src="/git&github/img/33.png"></p><br>
<br><p align="center"><img src="/git&github/img/34.png"></p><br>

<br>

\- develop 브랜치로의 이동과 병합

```
$ git checkout develop
$ git merge --no-ff hotfixes/1.1
```

<br><p align="center"><img src="/git&github/img/35.png"></p><br>
<br><p align="center"><img src="/git&github/img/36.png"></p><br>

<br>

\- master 브랜치로의 이동과 병합

```
$ git checkout master
$ git merge --no-ff hotfixes/1.1
```

<br><p align="center"><img src="/git&github/img/37.png"></p><br>

<br><p align="center"><img src="/git&github/img/38.png"></p><br>

<br>

\- 출시 버전 태그달기

```
$ git tag 1.1
```

<br><p align="center"><img src="/git&github/img/39.png"></p><br>

<br>

\- hotfixes/1.1 브랜치 삭제

```
$ git branch -d hotfixes/1.1
```

<br><p align="center"><img src="/git&github/img/40.png"></p><br><br>

이렇게 1.1 버전을 바로 출시한다.

<br><br>

### **이런 과정을 도와주는 도구 중 하나 "git flow"**

<br><br>

### **참고 사이트)**

[A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
