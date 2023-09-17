# Git 사용법(기본)

- terminal 열기
## 1. 깃 저장소 생성
- git init : 현재 디렉토리를 git 저장소로 사용

## 2.  초기 설정
- git config --global user.name "깃닉네임"
- git config --global user.email "깃이메일"

## 3. 스테이징에 올릴 파일 선택
- git add . : 모든 파일 스테이징에 올리기
- git add 파일명 : 선택된 파일만 올리기

## 4. 워킹트리 상태 확인
- git status / git status -s (요약해서 확인)
 : 현재 워킹트리 (스테이징 상태인 파일, 아닌 파일 확인)

## 5. 스테이징 상태 취소
- git rm --cached 파일명 / git rm --cached .
 : git add로 올려놓은 파일 다시 끌어내리기

## 6. 커밋
- git commit -m "작성할 메모"
 : 스테이징 area에 있는 파일 commit

## 7. 커밋내용 확인
- git log / git shortlog (요약해서 확인)

## 8. 현재 파일과 커밋된 파일 비교
- git diff : 변경사항 있는경우 출력 

## 9. 원격저장소 추가
- git remote -v
 : 깃 원격저장소 확인
- git remote add 이름(origin) 저장소주소 
 : 깃 원격저장소 주소 업데이트
- git remote get-url 이름(origin)
 : 원격저장소 주소 가져오기
- git remote rm 이름(origin)
 : 원격저장소 제거 

## 10. 원격저장소에 작업물 올리기(push)
- git push -u origin main (main은 branch 이름)
: 원격저장소에 push하여 업데이트
-> 만약 다른 작업자가 작업물을 수정 후 push하는 경우 오류 발생
-> pull 후에 push 해야 함. 

만일 git 원격저장소에 이미 올라간(push) 파일을 삭제하고 싶은경우
 : git rm 파일 -> 원격저장소, 로컬저장소에 있는 파일 삭제
 : git rm --cached 파일 -> 원격 저장소에 있는 파일만 삭제
위 작업 이후 git commit / git push 를 수행하여야 한다.

## 11. pull 과 clone (원격저장소 작업물 불러오기)
- git pull origin main
 : 깃 저장소에 있는 작업물 불러오기 
- git pull origin main --allow-unrelated-histories
 : 로컬 저장소와 원격 저장소 간의 이력이 서로 다른경우 사용 

- git clone 원격저장소주소
 : 깃 저장소에 있는 작업물 복사

(pull vs clone 차이)
clone : 로컬 저장소의 내용이 원격 저장소의 내용과 일치 -> 기존 작업 내용 삭제
pull : 원격 저장소의 내용을 가져와 현재 브랜치와 병합(merge)

 * pull은 병합과정이 있으므로 pull 전에 commit을 하지 않는 경우 덮어쓰기 에러 발생
-> 기존 작업에 대해 commit 후 pull 하는 습관을 들이자

---

# Git 협업

## 1. 브랜치 생성
- git branch 브랜치명 : 신규 브랜치 생성
- git branch : 브랜치 목록 확인 (활성 브랜치 *로 표시)

## 2. 작업 브랜치 변경
- git checkout 브랜치명 : 원하는 브랜치로 변경
- git switch 브랜치명

## 3. 각 브랜치 작업 후 병합
(작업 한 branch에서 commit 완료 후 -> main branch에서 아래 작업 실행)
- git merge 병합 할 브랜치명

## 각 브랜치에서 작업 후 main branch에서 merge실행
* merge 실행 후 헷갈리지 않도록 브랜치를 삭제해주는 것이 좋음


## 4. 브랜치 삭제
- git branch -D 브랜치명

** Merge시 다른 브랜치가 같은파일, 같은 라인에 수정을 하는경우 Conflict 발생하므로 같은파일을 다른 브랙치가 작업하지 않도록 하자! 

## 5. add / commit 취소
- git reset HEAD 파일명 / git restore --staged 파일명: add 취소

- git reset 커밋번호6자리 / git revert 커밋번호6자리 : 커밋번호는 git log에서 확인 가능
 : reset은 로그를 남기지 않고 revert는 로그를 남김
* 협업하는 경우 revert 지향
