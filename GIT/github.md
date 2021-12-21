# Github
원격 서버
1) Github 회원가입
2) 저장소 생성
***

## 원격 서버
Local Repository |push--><br/><br/><--pull|Remote Repository
---|:---:|---

### 원격 서버 주소 설정
`git remote add origin [원격 서버 주소]`<br/>
**origin** : remote repository (원격 저장소) 이름, 다른 이름도 무관<br/>
*원격 서버 주소 : github에서 확인*

#### 원격 저장소 확인
`git remote -v`

#### 원격 저장소 이름 변경
`git remote rename [기존이름] [새로운이름]`<br/>
원격 저장소의 브랜치 이름도 변경됨

#### 원격 저장소 삭제
`git remote rm [저장소이름]`
***

## push
- 로컬 저장소 변경 내용을 원격 서버로 보내기<br/>
  `git push [원격 저장소 이름] [push할 가지 이름]`<br/>
  `git push origin master`<br/>
- 전송되지 않을 때 강제 전송<br/>
  `git push origin master -f`

## pull
- 로컬 저장소를 원격 저장소에 맞춰 갱신<br/>
  `git pull`<br/>
- 원격 저장소의 변경 내용이 로컬 작업 디렉토리에 받아지고(fetch), 병합(merge)
***

## 삭제
> #### 원격 저장소에서 파일 삭제
github remote에 push한 파일은 **로컬의 저장소에서 파일을 삭제**해도<br/>
<u>원격 저장소에서는 삭제되지 않음</u>

> #### 원격 저장소와 로컬 저장소에 있는 파일 삭제
    git rm [File Name]

> #### 원격 저장소에 있는 파일 삭제 & 로컬 저장소에 있는 파일 보존
    git rm -cached [File Name]


    #### 파일 삭제
        git rm --cached 폴더명/파일명 확장자

    #### 폴더 하위의 모든 파일 삭제
        git rm --cacehd -r 폴더명/
***