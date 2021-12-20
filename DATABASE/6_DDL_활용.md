# DDL 활용
작성일시: 2021년 11월 23일 오후 5:18

## DDL (Data Definition Language)

데이터를 정의하는 언어

정의할 수 있는 대상 : schema, domain, table, view, index

---

## 생성 create

### DB 생성

```sql
create database front
  default character set utf8
  default collate utf8_general_ci;
```

### DB 선택

```sql
use front;
```

### 테이블 생성

```sql
**1. 새로운 테이블 만들기**
create table 테이블이름(
  필드명 데이터타입(길이) 제약,
  필드명 데이터타입(길이) 제약,
  필드명 데이터타입(길이) 제약,
  필드명 데이터타입(길이) 제약
);
```

```sql
**2. 다른 테이블을 이용한 테이블 생성**
  create table 테이블이름 as select문;
```

### Example

```
=========================================
게시판 : board
-----------------------------------------
항목 | 열 이름 | 데이터타입(길이) | 제약
-----------------------------------------
글 번호 | idx | int | PK, AI
제목 | title | varchar(100) | NN
내용 | content | text | NN
작성자 | author | varchar(20) | NN
작성일자 | wr_date | date | NN
조회수 | view_count | int | default 0
-----------------------------------------
=========================================
```

```sql
create table board(
  idx int primary key auto_increment,
  title varchar(100) not null,
  content text not null,
  author varchar(20) not null,
  wr_date date not null,
  view_count int default 0
);

//

create table board2 as select title, content, author from board;
*(게시물이 있다면 그 글도 같이 복제가 됨.)*
```

### 테이블 목록 확인

```sql
show tables;
```

### 테이블 구조 확인

```sql
describe 테이블이름
desc 테이블이름
```

---

## 수정 alter

### 1. 열 삭제

```sql
alter table 테이블이름 drop 삭제할 열이름

ex) alter table board drop view_count;
```

### 2. 열 추가

```sql
alter table 테이블이름 add 열이름 자료형

ex) alter table board add view_count varchar(20);

alter table 테이블이름 add 열이름 자료형 after 필드명; //특정 필드뒤에 추가
alter table 테이블이름 add 열이름 자료형 first;
```

### 3. Data type 변경

```sql
alter table 테이블이름 modify 열이름 자료형

ex) alter table board modify view_count int default 0;
```

### 4. 필드명 변경

```sql
alter table 테이블이름 change 기존열이름 새로운열이름 자료형
```

### 5. 테이블 이름 변경

```sql
1. rename table 이전이름 to 새로운이름
  ex) rename table board to notice;

2. alter table 이전이름 rename 새로운이름
  ex) alter table notice rename event;
```

---

## 삭제 drop

### 1. 테이블 데이터 삭제 (DML : delete)

```sql
1. truncate table 테이블이름
  ex) truncate table event;
```

### 2. 테이블 삭제

```sql
1. drop table 테이블이름
  ex) drop table board2;
```

---

## 제약조건 변경

### 1-1. 일반 제약조건 추가

```sql
alter table 테이블이름 add constraint 제약조건이름 제약조건(열이름);
```

### 1-2. Foreign key 추가

```sql
alter table 테이블이름 add foreign key (열이름) references 참조테이블이름(열이름);;
```

### 2. 제약조건 삭제

```sql
alter table 테이블이름 drop constraint 제약조건이름;
alter table 테이블이름 drop foreign key 제약조건이름;
```

<aside>
💡 제약조건이름은
`select * from information_schema.table_constraints;`  또는
`select * from information_schema.table_constraints where table_name = '테이블명';` 에서 확인가능하다.

</aside>

### 3. 제약조건 비활성화

```sql
alter table 테이블이름 disable constraint 제약조건이름;
```

### 4. 제약조건 활성화

```sql
alter table 테이블이름 enable constraint 제약조건이름;
```

---