# DML 활용
작성일시: 2021년 11월 24일 오후 3:11

## DML (Data Manipulation Language)

데이터를 조작하는 명령어

유형 : insert / select / update / delete

---

## 데이터 삽입 insert

삽입 형태로신규 데이터를 테이블에 저장

### 1. 전체 필드에 데이터 입력

```sql
insert into 테이블 이름 values('값1', '값2', ...)

ex) insert into board values(1, '첫번째 글', 'aaaaaa', '관리자', '2021-11-24', 0);
```

<aside>
💡 idx, view_count에는 `제약조건`때문에 `**값**`을 안줘도 됨.

</aside>

### 2. 일부 필드에 데이터 입력

```sql
insert into 테이블이름(필드명1, 필드명2, ...) values('필드1의 값1', '필드2의 값', ...)

작성 순서는 표의 순서를 지키지 않아도 됨.
ex) insert into board(title, content, author, wr_date) values('두번째 글', 'bbbbbb', '홍길동', '2021-11-24')
```

<aside>
💡 ★필드명의 수와 값의 수가 같아야 한다.

</aside>

---

## 데이터 조회 select

테이블의 내용을 조회

### 1. 전체 데이터 검색

```sql
seleect * from 테이블이름

ex) select * from board;
```

### 2. 일부 데이터 검색

```sql
select 필드명, 필드명, ... from 테이블이름

ex) select idx title from board;
```

### 3. 중복값 제외 검색

```sql
select distinct 필드명 from 테이블이름

ex) select distinct title from board;
```

### 4. 별칭 사용

```sql
select 필드명 as 별칭, 필드명 as 별칭, ... from 테이블이름

ex) select title as '제목', content as '내용' from board;
// 테이블의 필드명이 바뀐 것은 아니고 출력될 때만 별칭으로 보임.
```

### 5. where절 : 조건 검색

```sql
select 필드명 from 테이블이름 where 조건

ex) select * from board where idx=1;
    select title, content from board where idx=1;
    select * from board where author='관리자';
```

### 6. in : 비연속 범위 검색

```sql
select 필드명 from 테이블이름 where 조건필드 in(검색조건, 검색조건, ...)

ex) select * from board where idx in(1, 3, 5);
```

### 7. between ~ and : 연속 범위 검색

```sql
select 필드명 from 테이블이름 where 조건필드 between 최초범위 and 최종범위

ex) select * from board where idx between 1 and 5;
    select * from board where wr_date between '2021-11-22' and '2021-11-24';
```

### 8. order by asc(오름차순)/desc(내림차순) : 정렬

```sql
select 필드명 from 테이블명 order by 기준필드 정렬방식

ex) select * from board order by idx desc;
    select * from board where idx in(1, 3, 5) order by idx desc;
```

---

## 데이터 변경 update

테이블의 내용을 변경

### 1. 단일 필드 수정하기

```sql
update 테이블이름 set 필드명='수정할 값'

ex) update board set view_count=1;
```

### 2. 여러 필드 수정하기

```sql
update 테이블이름 set 필드명='수정할 값', 필드명='수정할 값',...
```

### 3. 조건에 해당하는 필드 수정하기

```sql
update 테이블이름 set 필드명='수정할 값', 필드명='수정할 값',... where 조건

ex) update board set view_count=2 where idx in(1, 3, 5);
```

---

## 데이터 삭제 delete

테이블의 내용을 삭제

### 1. 단일 필드 삭제하기

```sql
delete from 테이블이름

ex) delete from board;
```

### 2. 조건에 해당하는 필드 삭제하기

```sql
delete from 테이블이름 where 조건

ex) delete from board where idx in(1, 3, 5);
```

---