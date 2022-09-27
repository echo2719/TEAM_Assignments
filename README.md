5.1 🚀 서버 저장소
=
## 5.1.1 협업 저장소

깃은 여러 개발자와 협업하려고 탄생한 도구이다.
- 여러 명이 같이 협업하여 개발하면 적은 시간으로 좀 더 좋은 품질의 소프트웨어를 만들 수 있다.
- 인터넷에 연결하는 작업 환경과 인터넷에 연결하여 작업할 수 없는 두가지 개발 환경을 고려하여 분산형 모델을 선택했다.

## 5.1.2 연속된 작업

깃은 분산된 저장소 여러 개를 하나로 통합하고 최신코드 배포가 가능하다.
- 사무실에서 작업을 하고 서버에 올리고 서버에 올렸던 코드를 로컬 컴퓨터에 동기화하여 연속된 작업이 가능하다.
- 서버 저장소는 여러 컴퓨터에 동일한 깃 저장소를 복제, 작업한 결과물을 다시 서버로 통합한다.

## 5.1.3 새 멤버

깃의 분산형 관리 체계는 다수의 사람과 협업하는 데 용이하다.
- 새로운 멤버가 기존 프로젝트에 참여 시, 현재까지 작업한 소스 코드 마지막 버전을 공유해야 한다.
- 기존에 코드 공유는 이메일, 외부 저장 장치 등을 이용 -> 깃의 원격 저장소 주소만 알려주면 해결된다.
- 원격 저장소로 모든 구성원에게 코드의 최종 결과물 동기화한다.

* * *

5.2 🚀 깃허브 서버 준비
=
## 5.2.1 깃허브
	1. 회원가입을 위한 이메일 주소 입력이 필요하다.
	2. 저장소를 구별하는 주소 값으로 사용될 사용자 이름(영문) 작성 필요하다.
- 깃허브는 깃호스팅 서비스이다.
- 모든 서비스를 회원가입 후 무료로 사용이 가능하다.
- 깃허브 공식 사이트 : http://github.com

## 5.2.2 저장소 생성
>1. 깃허브에 로그인한다.
>2. 오른쪽 상단에 + 모양 메뉴에서 New repository 버튼을 클릭한다.
>3. 새 저장소 생성 화면으로 전환 후 저장소를 생성할 소유자를 Owner에는 개인 게정이나 생성한 조직을 선택한다.
>4. Repository name에는 저장소 이름을 대·소문자, 숫자, 하이픈, 밑줄을 조합하여 원하는 이름 입력한다.
>5. Create repository 버튼을 클릭하여 저장소 생성한다.
- 공개용 저장소로 생성하여 실습한다.
- 공개된 저장소는 무제한 생성 가능하다.
- 비공개용 저장소는 제약이 있고, 일부는 유료 서비스이다.
- https://github.com/소유자/저장소로 표기된다.
- 한 소유자 안에서 같은 저장소 이름은 중복 생성 불가능하다.

---

5.3 🚀 깃허브 연동 및 원격 등록
=
5.3.1 로컬 저장소
-
원격 저장소에 연결하려면 로컬 저장소가 있어야 한다.    
로컬 저장소를 원격 저장소에 연결하는 방법에는 2가지가 있다.
> 1. 새 로컬 저장소 생성 후 원격 저장소 연결하는 방법
> 2. 기존 저장소를 연결하는 방법
     **이 책에는 1번만을 알려준다.**    
     $mkdir gitstudy05 -> gitstudy05라는 새 폴더 만들기.
     $cd gitstudy05 -> 현재 위치를 gitstudy05로 바꾸기.
     $git init -> 저장소를 깃으로 초기화....
     $echo “# gitstudy05” >> README.md -> 저장소의 소개 페이지 파일 생성.
     $git add README.md -> 스테이지에 등록
     $git commit –m “first commit” -> 커밋, 커밋 메모: “first commit”


## 5.3.2 프로토콜
서버와 통신하기 위한 Locla, HTTP, SSH, Git 이 네 종류의 전송 지원 방식을 지원한다.
1. Local(로컬)
> 로컬 컴퓨터에 원격 저정소를 생성한다.
>> 폴더 경로만 입력하면 된다. ($ git remote add 원격저장소별칭 폴더경로)

2. HTTP
> 기존 아이디와 비밀번호만으로 접속자를 인증할 수 있다. 익명, 계정을 이용해 처리도 할 수 있다.

3. SSH
> 깃에서 권장하는 프로토콜이다. 인증서 중 공개키는 서버에 등록하고 개인키는 로컬에 저장한다.

4. Git
> 깃을 위한 전용 프로토콜 방식이다. 보안에 취약하다.

## 5.3.3 원격 저장소의 리모트 목록 관리
**remote : 깃의 서버 관리**
> 등록, 취소등 작업이 가능하다.

1. $git remote -> 원격 저장소의 이름(별칭) 출력
2. $git remote –v -> 원격 저장소의 이름(별칭)과 URL 출력 **저장소의 권한 정보는 알 수 없다.**

## 5.3.4 주소와 별칭
로컬 저장소에 원격 저장소를 등록하려면 서버 주소가 필요하다.
로컬에 서버 저장소 생성시에는 폴더 경로로도 사용이 가능하다.
**별칭 : 서버 주소가 길기 때문에 쉽게 작업하려고 사용하는 별명이다. 대표적으로 origin이 있다.**

## 5.3.5 원격 저장소에 연결
**add 옵션을 사용한다.**
> $ git remote add 원격저장소별칭 원격저장소URL
>> $git remote add origin 자신의 서버 주소
>> $git remote –v : 원격 저장소 목록 확인

**원격 저장소가 연결되면 fetch와 pust 두 주소를 출력한다.**
- pust는 서버로 전송
    - fetch는 서버에서 가져옴 이다.

## 5.3.6 소스트리에서 원격 브랜치
원격 저장소를 등록하면 기존 master브랜치와 달리 또 하나의 브랜치가 **자동으로 생성된다.**.
> master --> 현재 로컬 저장소 브랜치
> local/master  --> 원격 저장소 브랜치
>> 이로 서로 동기화한 시점을 판별할 수 있다.
###### 브랜치는 나중에 설명한다.

## 5.3.7 별칭 이름 변경과 정보
rename : 별칭 바꾸기
> $ git remote rename 변경전 변경후

show : 원격 저장소의 상상한 정보 확인
> $ git remote show 원격저장소별칭

## 5.3.8 원격 서버 삭제
rm : 임시 등록된 원격 저장소 삭제
> $ git remote rm 원격저장소별칭

---

# 5.4 🚀 서버 전송

## 5.4.1 Push : 서버에 전송
* 푸시(push)는 커밋된 파일을 원격저장소로 업로드하는 동작이다.
* $ git remote -v 명령어로 연결된 저장소와 서버목록 확인한다.
* $ git push 원격저장소별칭 브랜치이름 입력한다.
* Master 브랜치에 현재 브랜치를 업로드 한다.
* 협력 목적이 아닌 로컬 저장소 백업용도로도 사용 가능하다.

---


5.5 🚀 원격 저장소에서 커밋된 코드를 내려받기
=
## 5.5.1 clone: 복제
    git clone [원격 저장소 URL]
- 초기화 init 명령어 외에 **원격 서버 접속에 필요한 추가 설정을 자동으로 수행한다.**
- 서버의 연결 설정을 마친 후 서버 안에 있는 **모든** 커밋된 코드 이력들을 한번에 내려받는다.
> 기존 저장소를 이용하여 새로운 저장소를 생성하는 방법중 하나로, 그냥 복제하는 것과는 다른 개념이다.

### 원격 저장소의 정보를 확인
	git remote -v
## 5.5.2 pull : 서버에서 내려받기

복제는 원격 저장소에서 모든 내용을 **한 번**에 내려받는다.

복제 후 **원격 저장소의 갱신된 내용을 추가로 내려받으려면 pull 명령어를 사용해야 한다.**

	git pull

- pull 명령어는 로컬 저장소보다 최신인 갱신된 원격 저장소의 커밋 정보를 현재 로컬 저장소로 내려받는다.
> pull 명령어를 주기적으로 사용하면 최신 커밋 정보로 로컬 저장소를 유지 가능하다. 또한 원격 저장소와 로컬 저장소 간 커밋을 반영할 수 있다.

---

5.6 🚀 수동으로 내려받기
=
5.6.1 자동병합
-
pull은 __원격 서버에서 현재 커밋보다 최신 버전이 있을 경우__ 내려받는다내려받은 최신 커밋은 __현재 브랜치로 자동 병합을__ 한다.
여기서 여러 개발자와 협업을 할 경우 자동으로 브랜치를 병합을
못하고 __충돌하는 일이__ 생겨 수동으로 내려받아야 한다.
>pull 명령어로 자동 병합을 하지 못할때는 수동으로 받아야 한다.

5.6.2 fetch:가져오기
-
원격 저장소에서 코드를 __수동으로 내려받는 작업__ 이다

    git fetch 원격저장소URL
- Fetch 명령어는 원격 저장소에서 최신 커밋을 임시 브랜치로 내려 받는다.
- 여기서 브랜치는 자동으로 병합되지 않는다.

5.6.3 merge로 수동 병합
-
fetch로 받은 __커밋을 로컬로 적용하기__ 위해 merge를 사용한다.

    git merge 원격저장소별칭/브랜치이름

- merge 명령어를 실행하고  log를 확인하면 로컬에서 확인이 가능하다.

---

# 5.7 🚀 순서

**원격저장소는 다수 개발자가 동시에 커밋 푸시가 불가하므로, 협업 시 순차적으로 푸시 가 필요하다**

## 5.7.1 최신 상태
* 푸시 전 로컬저장소를 최신 상태로 업데이트한다.
* 커밋이 순차적이지 않을 때, 깃 자체적으로 푸시 명령 거부된다.
* 푸시 작업 거부되었을 시, fetch 작업으로 로컬저장소 갱신 필요하다.

## 5.7.2 충돌 방지
* 최신상태에서 푸시를 허용하는 것은 충돌을 방지하기 위함이다.
* % 풀작업은 커밋들을 현재 브랜치로 자동병합하는 방법으로 이때, 커밋의 내용이 순차적이지 않을 경우 충돌 발생한다.
* 로컬저장소와 원격저장소를 항상 최신으로 유지해야 충돌을 방지할 수 있다.


# 5.8 정리
* 깃은 버전관리 프로그램이기 이전에 협업도구로 사용하므로 협업을 위해 매개체 역할을 수행할 서버가 필요하다.
* 다양한 서버를 지원함으로써 직접 생성 혹은 인기 깃 호스팅 서비스 사용 가능하다.
* 불특정 다수를 대상으로도 공유가 가능하여 현재 깃은 오픈소스를 활성화 하는데 가장 많은 기여를 한 협업툴로 등극되었다.
