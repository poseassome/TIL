# DB 명령어
작성일시: 2021년 11월 18일 오후 4:40

## DB 명령어

1. **DCL**
- 사용자 권한 설정 및 회수
- grand, revoke
   권한부여 명령어 / 권한회수 명령어
2. **DDL**
- 데이터 객체 제어
- create, alter, drop
3. **DML**
- 데이터 조작
- insert, update, delete, select

|  | NEW | EDIT | REMOVE | SEARCH |
| --- | --- | --- | --- | --- |
| DDL | create | alter | drop |  |
| DML | inset | update | delete | select |

---

## MariaDB 기본 쿼리

1. show : 데이터베이스 & 테이블 목록 확인
2. use : 데이터베이스 선택

---

### 데이터베이스 생성하기

> **`create`**

1) 객체 생성
    - DB, table, 사용자, index, ...
2) 기본 문법
    - `create 객체 객체명 (하위 요소)`
3) DB 생성
    - `create database DB명;`
>

**데이터베이스 생성 전**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6c27c94d-fb99-403d-b7bd-6de0fc1131ff/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082600Z&X-Amz-Expires=86400&X-Amz-Signature=9c048cc4bffa8ac690dc8d58b38eecdb04e348b6cf6f6fb8e393136d7dae7228&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

**데이터베이스 생성 코드 작성**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d19dfa60-4c5d-4441-aa1e-f64880887cf1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082608Z&X-Amz-Expires=86400&X-Amz-Signature=22614acfefebdc33ae4d24ee9646d16dcdad7f7870d030503287665dddee32c2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

```
create database frontend
-> default character set utf8
-> default collate utf8_general_ci;
```

**데이터베이스 생성 후**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53bbde32-3315-4a30-92d6-18f8657e79a4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082617Z&X-Amz-Expires=86400&X-Amz-Signature=56d94af754a6eb7782ab3422a64704dbcb9706b768c57e4c15c564f095c02471&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

### 데이터베이스 삭제하기

> `**drop**`

1) DB 삭제
    - `drop database DB_NAME;`
>

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6f51a279-ead4-40b4-9aa8-7bb65a1abc3a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082624Z&X-Amz-Expires=86400&X-Amz-Signature=71d107614e691931f0e4e12441d4def01fb45e65c814d6aa33acf5b32fb7b25e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---