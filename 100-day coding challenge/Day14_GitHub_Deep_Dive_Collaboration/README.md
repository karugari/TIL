# Day 14: GitHub Deep Dive Collaboration

## 1. `git clone`과 PAT의 재발견

### ① GitHub에서 비밀번호 대신 토큰(PAT)을 사용하는 이유
- **보안의 세분화**: 비밀번호는 계정의 모든 권한을 갖지만, 토큰은 특정 저장소 읽기/쓰기 등 **원하는 권한(Scopes)**만 선택적으로 부여 가능합니다.
- **유출 시 통제**: 토큰 유출 시 해당 토큰만 삭제(Revoke)하면 계정 전체를 안전하게 보호할 수 있습니다.
- **표준 인증 수단**: 터미널이나 외부 소프트웨어에서 로그인할 때 Password 대신 입력하는 값이 바로 이 토큰입니다.

### ② 저장소 복제하기: `git init` vs `git clone`
- **`git init`**: 빈 폴더를 새로운 저장소로 초기화합니다. (로컬에서 새로 시작할 때)
- **`git clone [URL] .`**: 이미 존재하는 원격 저장소를 통째로 복제합니다. 모든 커밋 이력이 포함되며, 원격지(`origin`)가 자동으로 연결됩니다.



### ③ 자격 증명 관리 (Credential Management)
계정 전환이나 보안 갱신 시 저장된 인증 정보를 초기화하는 명령어입니다.

- **macOS (키체인 삭제)**:
    1. `git credential-osxkeychain erase`
    2. `host=github.com`
    3. `protocol=https`
    4. (Enter 두 번)
- **Windows (CLI 자격 증명 삭제)**:
    1. `git credential reject`
    2. `host=github.com`
    3. `protocol=https`

---

## 2. 프로젝트 협업: Collaborators & Syncing

### ① 비공개 저장소와 협업자 초대
- **개념**: 기밀/내부 프로젝트를 위해 비공개(Private) 저장소를 운영하고 특정 인원에게만 접근 권한을 부여합니다.
- **초대 방법**: `Settings` -> `Collaborators` -> `Add people` (닉네임/이메일 초대) -> **상대방의 수락(Accept)** 필수.

### ② 협업 워크플로우
협업자로 등록되면 소유자가 아니더라도 해당 저장소에 직접 쓰기 권한을 갖게 됩니다.
1. `git clone [URL] .` (저장소 복제)
2. 코드 수정 후 `git add` -> `git commit`
3. `git push origin main` (**본인의 PAT를 사용하여 인증**)

### ③ 코드 동기화: `git pull`
팀원이 원격 저장소에 올린 최신 코드를 내 로컬 저장소로 업데이트합니다.
- **`git push`**: 로컬의 변경 사항을 원격으로 전송 (Local → Remote)
- **`git pull`**: 원격의 변경 사항을 로컬로 가져와 합침 (Remote → Local)
- **핵심 팁**: 작업을 시작하기 전이나 수시로 `git pull`을 실행하여 코드 격차와 충돌을 최소화해야 합니다.

---

## 3. 오픈 소스의 꽃: Forks & Pull Requests

### ① 오픈 소스 기여(Contribution)란?
협업자(Collaborator) 권한이 없는 외부 개발자가 공개된 프로젝트의 버그를 수정하거나 기능을 추가하여 제안하는 과정입니다.

### ② 기여의 5단계 프로세스
1. **포크 (Fork)**: 타인의 저장소를 내 계정으로 통째 복제하여 소유권을 확보합니다.
2. **복제 (Clone) & 수정**: 내 계정의 포크된 저장소를 로컬로 내려받아 수정합니다.
3. **푸시 (Push)**: 수정본을 내 원격 저장소(Forked Repo)에 업로드합니다.
4. **풀 리퀘스트 (Pull Request, PR)**: 원본 저장소 소유자에게 내 변경 사항을 병합해달라고 제안합니다.
5. **검토 및 병합 (Review & Merge)**: 원본 관리자가 코드를 검토 후 승인하면 최종 프로젝트에 반영됩니다.
