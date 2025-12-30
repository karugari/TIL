# Day 11: Web Deployment, Path Management, and Version Control Basics
## 1. 내 웹사이트 세상에 공개하기 (Deployment)
로컬 컴퓨터에서 작성한 코드를 전 세계 사용자가 접속할 수 있는 환경으로 만드는 과정을 학습했습니다.

배포(Deployment)와 호스팅(Hosting)의 개념
배포(Deployment): 로컬 환경의 코드(HTML, CSS, JS)를 원격 컴퓨터인 '서버'로 이전하여 서비스를 활성화하는 행위.
호스팅(Hosting): 서버의 일정 공간을 빌려 웹사이트 파일이 안전하게 머무를 수 있게 하는 서비스. (집을 빌리는 것과 유사)
서버(Server): 24시간 인터넷에 연결되어 클라이언트의 요청을 기다리고 리소스를 응답하는 원격 컴퓨터.

웹의 작동 원리 (Request-Response Cycle)
요청(Request): 브라우저에 주소를 입력하면 해당 서버에 필요한 파일을 요청함.
응답(Response): 서버는 요청을 확인하고 저장된 HTML, CSS 파일을 브라우저로 전송함.
렌더링(Rendering): 브라우저는 받은 명령문(Code)을 해석해 시각적인 화면으로 그려냄.

## 2. 웹사이트의 디테일: 파비콘(Favicon)
정의: 브라우저 탭 제목 옆에 표시되는 '사이트 대표 아이콘'.
특징: 브라우저는 자동으로 루트 폴더의 favicon.ico를 검색함. 파일이 없을 경우 개발자 도구에서 404 에러를 발생시킴.
적용: 특수 아이콘 형식으로 변환 후 아래 코드로 연결.

```HTML
<link rel="icon" href="images/favicon.ico" type="image/x-icon">
```
## 3. 경로 관리 (Relative vs Absolute Path)
프로젝트 규모가 커지고 하위 폴더가 생성될 때 리소스 깨짐 현상을 방지하기 위한 필수 지식입니다.

구분	정의	특징	장단점
상대 경로	현재 파일 위치 기준	./images/logo.png	파일 이동 시 경로가 깨질 위험이 큼
절대 경로	루트 폴더 기준	/styles/style.css	시작 부분에 / 추가. 파일 위치와 무관하게 고정됨

## 4. Git & GitHub
단순한 파일 복사가 아닌 '진화'하는 코드를 관리하기 위한 버전 관리(Version Control) 시스템입니다.

### Git (로컬 버전 관리 도구)
- Repository: 모든 프로젝트 기록이 담긴 저장소.
- Commit: 현재 상태를 기록하는 '스냅샷'. (세이브 포인트)
- Branch: 원본을 유지하며 새로운 기능을 실험하는 '가지치기'.

### GitHub (원격 협업 플랫폼)
- Remote Repo: 클라우드에 저장된 Git 프로젝트.
- Clone: 원격 저장소를 내 컴퓨터로 복제해오기.
- Pull Request: 내가 수정한 코드를 원본에 반영해달라고 제안하기.


## 5. 인간-컴퓨터 상호작용: GUI vs CLI

CLI (Command Line Interface)를 선택하는 이유
효율성: 복잡한 클릭 과정을 명령어 한 줄로 단축 가능.
전문성: 서버 환경이나 고급 Git 조작은 CLI가 표준임.
환경 제약: 모니터나 마우스가 없는 실제 배포 서버 제어에 필수적.

