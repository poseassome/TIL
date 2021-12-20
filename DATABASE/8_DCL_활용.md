# DCL 활용
작성일시: 2021년 11월 24일 오후 4:01

## DCL (Data Control Language)

데이터베이스에서 데이터 이외의 오브젝트에 대해 조작하는 SQL명령

조작 대상 : 사용자권한 / 트랜잭션

---

## 사용자 권한 부여 grant

권한은 시스템 권한과 객체 권한으로 분류

### 1. 시스템 권한

```sql
grant 권한, 권한 to '아이디'@'접속위치';

// with 옵션은 권한을 받는 사용자가 다른 사용자에 권한을 줄 수 있게 할 때 사용
   with grant option;
```

### 2. 객체 권한

```sql
grant 권한, 권한 on DB이름.테이블이름 to '아이디'@'접속위치';

ex) grant select, insert on front.* to 'tester1'@'localhost';
```

시스템 권한 종류

| 권한 | 내용 |
| --- | --- |
| create user | 계정 생성 권한 |
| drop user | 계정 삭제 권한 |
| drop any table | 테이블 삭제 권한 |
| create session | 데이터베이스 접속 권한 |
| create table | 테이블  생성 권한 |
| create view | 뷰 생성 권한 |
| create sequence | 시퀀스 생성 권한 |
| create procedure | 함수 생성 권한 |

객체 권한 종류

| 권한 | 내용 |
| --- | --- |
| alter | 테이블 변경 권한 |
| insert | 데이터 조작 권한 |
| delete | 데이터 조작 권한 |
| select | 데이터 조작 권한 |
| update | 데이터 조작 권한 |
| execute | procedure 실행 권한 |

---

## 사용자 권한 회수 revoke

### 1. 시스템 권한

```sql
revoke 권한 from '사용자'@'접속위치'
```

### 2. 객체 권한

```sql
revoke 권한 on DB.table from '사용자'@'접속위치'

ex) revoke all on *.* from 'tester1'@'localhost';
```

---

## 트랜잭션 transaction (TCL 명령어)

일 처리 단위 / 트랜잭션 결과를 수용하거나 취소

### 1. commit

```sql
거래 내역을 확정함.
```

### 2. rollback

```sql
거래 내역을 취소함.
```

### 3. checkpoint

```sql
저장점 설정 (ROLLBACK할 위치를 지정함.)
```

### 4. 트랜잭션 제어 SQL문

```sql
START TRANSACTION;
savepoint a;
INSERT INTO `salaries` (emp_no, salary, from_date, to_date) VALUES (1001,900 ...);
savepoint b;
UPDATE salaries set salary = 1000 where emp_no = 1001;
rollback to b;   // update 취소된 상태로 돌아감
rollback to a;   // insert 취소된(데이터가 없는) 상태로 돌아감
```

### 5. auto commit

트랜잭션 명령문에 COMMIT이 없어도 DML 문이 성공적으로 수행되면 자동으로 COMMIT되며, 또한 DML문이 실패하면 자동으로 ROLLBACK이 되는 기능

```sql
SELECT @@AUTOCOMMIT;

이 명령의 결과가 1이면 Auto Commit이 설정된 것을 의미한다.
```

```sql
SET AUTOCOMMIT = TRUE; -- Auto Commit 설정
SET AUTOCOMMIT = FALSE; -- Auto Commit 해지
```

---