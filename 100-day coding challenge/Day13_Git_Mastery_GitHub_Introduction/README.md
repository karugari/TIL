# Day 13: Git Mastery & GitHub Introduction

## 1. 가지치기와 병합 (Branching & Merging)
프로젝트의 안정성을 유지하며 새로운 기능을 개발하는 협업 프로세스를 학습했습니다.

### 브랜치 관리
- **이름 변경**: `git branch -m main` (Master에서 Main으로 표준화)
- **상태 확인**: `git branch` (`*`와 초록색은 현재 위치를 의미)
- **생성 및 이동**: `git checkout -b feature` (브랜치 생성과 동시에 이동)
- **HEAD**: 현재 보고 있는 브랜치의 가장 최신 커밋 포인터

### 병합(Merge) 및 충돌(Conflict) 해결
1. **이동**: `git checkout main` (기준 브랜치로 이동)
2. **병합**: `git merge feature`
3. **충돌 해결**: 같은 라인 수정 시 발생하는 `CONFLICT` 해결
    - **Accept Current Change**: 현재 브랜치(Main) 내용 유지
    - **Accept Incoming Change**: 가져올 브랜치(Feature) 내용 선택
    - **마무리**: 수정 후 `git add .` -> `git commit`으로 병합 커밋 생성

---

## ⏪ 2. 실수 되돌리기 및 삭제 (Reset & Revert)
데이터를 안전하게 관리하고 잘못된 기록을 복구하는 방법을 익힘

### 파일 및 브랜치 삭제
- **파일 삭제**: `git rm [파일명]` (물리적 삭제와 스테이징을 한 번에 처리)
- **브랜치 삭제**: `git branch -D [브랜치명]` (작업 완료 후 저장소 최적화)

### 변경 사항 복구 (Reset & Restore)
1. **커밋 삭제**: `git reset --hard HEAD~1` (최신 커밋과 파일 수정을 완전히 이전으로 되돌림)
2. **스테이징 전 취소**: `git checkout -- .` 또는 `git restore .` (수정 사항 폐기)
3. **스테이징 취소**: `git reset [파일명]`또는`git restore --staged [파일명]` (장바구니에서 다시 빼기)

---

## 🚀 3. 로컬에서 원격으로: GitHub 시작하기
내 컴퓨터의 프로젝트를 클라우드 저장소(Remote Repository)에 연결하여 전 세계와 공유합니다.

### GitHub의 가치
- **백업**: 하드웨어 고장 등 데이터 손실 대비
- **포트폴리오**: 개발자로서의 꾸준함과 실력을 증명하는 '개발자 신분증'
- **협업 및 기여**: 팀 프로젝트 수행 및 오픈 소스 생태계 참여

### 원격 저장소 연결 명령어
- **원격지 등록**: `git remote add origin [URL]` (`origin`이라는 별칭으로 주소 등록)
- **코드 업로드**: `git push origin main` (로컬의 기록을 원격으로 전송)
  
