# Database 개념, Access 사용
작성일시: 2021년 11월 17일 오후 2:28

# DataBase

`Data`를 사용할 수 있는 관련 프로그램을 설치하고,
그 안에 `Database(Data 집합)`를 만들고,
그 안에 직접적으로 Data를 저장하는 `table`을 생성한다.

우리는 **MySQL** 사용할 것 (정확히는 거기서 파생된 *MariaDB*)

**왜?** 프로그래밍 언어마다 어울리는 프로그램이 있다.

| 프로그래밍 언어 | DB |
| --- | --- |
| asp | MS-SQL |
| php | MySQL |
| jsp | Oracle |

---

## MicroSoft Office_Access

1. **Access 실행**
실행하면 '보기'에서 2가지가 있다.

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a996705a-648b-4f7e-95dd-5792c1879604/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082016Z&X-Amz-Expires=86400&X-Amz-Signature=84fac6a6353962a64e49bf244f8dfa9c40b32469bcf63d7b49b6758b7d0a10e5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    데이터시트 보기 : 데이터 만든 걸 보는 화면
    디자인 보기 : 데이터 만드는 화면

    디자인 보기로 'members' 이름의 `table` 생성

2. **필요정보 정리**
회원가입에 필요한 회원 정보 data를 만든다.

    ```
    ***웹 페이지에서 보이는 회원가입 시 필요한 항목**
      ------------------
      이름
      아이디
      아이디 중복확인
      비밀번호
      비밀번호 확인
      생년월일
      성별
      전화번호
      휴대폰 인증
      이메일
      우편번호 검색
      주소
      수신동의
      ------------------
    ```

    ```
    ***데이터베이스 테이블에서 필요한 정보**
      ------------------
      ★고유번호 (첫 번째 열은 무조건 !)
      이름
      아이디
      (X) 아이디 중복확인
    			---> 아이디 중복확인을 거친 아이디만 저장하게 되어있으니까 중복확인 여부는 필요없음
      비밀번호
      (X) 비밀번호 확인
    			---> 비밀번호확인은 사용자의 실수를 방지하기위해서 만든 것
      생년월일
      성별
      전화번호
      (X) 휴대폰 인증
      이메일
      (X) 우편번호 검색
    			---> 우린 우편번호가 필요한거지 우편번호 검색이 필요한건 아님
      우편번호
      (X) 주소
    			---> 주소 한 줄에 저장할 거 아니니까 기본, 상세 나누기
      기본주소
      상세주소
      수신동의
    			---> 수신동의를 보고 안내 메세지 발송결정하니까 (약관동의랑 헷갈리지 말 것)
      ------------------
    ```

    내게 필요한 `Data`만 찾아내고 수정하고 삭제하는 것이 가능해야 한다.
    그러면, 필요한 `Data`를 골라내는 방법이 필요하다.
    ==> `select ~~~ where` 조합(명령어)

    **`Data`를 구분하는 방법은?**
      *이름* - 동명이인 있어서 안 됨.
      *전화번호* - 전화번호 바꿀 수 있어서 안 됨.
      *아이디* - 관리자 실수, 시스템 오류 등으로 똑같은 아이디가 있을 수 있음.

    <aside>
    💡 그래서 필요하게 된 게 Access에서 **'ID'(고유번호, index 개념)** 이다.
    **모든 Database의 첫 번째 열은 고유번호이다.**

    </aside>

3. **데이터 표준 정의**

    table의 구성 - 행/ 열/ field/ fieldset

    ```
    데이터베이스 테이블 : members
    -------------------------------------------------------
    항목 | 필드명 | 데이터 타입(길이값) | 제약(규칙이나 옵션)
    -------------------------------------------------------
    고유번호 | idx | int | 자동증가, 기본 키
    이름 | u_name | varchar(10) | 빈 값 X <-- Not Null(NN)
    아이디 | u_id | varchar(20) | 빈 값 X
    비밀번호 | pwd | varchar(12) | 빈 값 X
    생년월일 | birth | date |
    성별 | gender | char(2) /알파벳으로 저장할거면 (1) |
    전화번호 | mobile | varchar(14) |
    이메일 | email | varchar(100) |
    우편번호 | postalCode | varchar(5) |
    기본주소 | addr1 | varchar(100) |
    상세주소 | addr2 | varchar(100) |
    수신동의 | agree | char(1) |
    ```

    - 일부 데이터타입은 길이값이 고정되어 있어서 작성하지 않아도 됨.
        ex) int : 4 아니면 8
    - 자동증가에는 중복불가가 포함되어있고 주 키(기본키, Primary key)가 설정되어 있음.
        1) **Primary key** : 이 부분의 data는 각각의 data를 구분할 수 있는, 다른 것들과 중복되지않은 data가 들어있는 곳이야 하고 알려주는 역할
        2) **Foreign key** : 다른 곳에서 참고하는 외래 키
    - **자동증가 field**는 한 `table`에 하나 밖에 만들지 못함.
    - *char*:고정길이 / *varchar*:가변길이
        char(10)일 때, 5글자 입력하면 나머지 5글자는 space(공백)으로 채움.
        varchar(10)일 때, 5글자 입력하면 그대로 저장함.
            **[속도]** char > varchar
            **[성능]** char < varchar
    - 전화번호는 숫자가 아니라 문자로 저장한다.
    숫자로 저장하면 맨 앞에 0 사라지고, 계산이 된다.
4. **Access 입력**

    **디자인 보기**에서 정리한 `Data` 입력하고

    ![데이터 형식과 필드크기, 빈 문자열 허용을 설정한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4e0f5a45-6cb1-4ba5-a27f-7f5e49eb30ed/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082028Z&X-Amz-Expires=86400&X-Amz-Signature=917cc9da3bae278513c17df3ba042fa9f6c8d2aabdca07ee3739c9f22ebd5c7a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    데이터 형식과 필드크기, 빈 문자열 허용을 설정한다.

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8612ffb5-806c-4851-a43b-5b0d3ac10737/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082038Z&X-Amz-Expires=86400&X-Amz-Signature=89a4330b2546e0cadfc0534356f5c85ee28f7519d27f9bda14ce0f60e22fc56f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    **데이터시트 보기**에서 정보 입력한다.

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5d421b42-493b-4320-b94f-3ecc741cb35d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082052Z&X-Amz-Expires=86400&X-Amz-Signature=45bc46d05447a444183291e10116ddbcebbd599f6e23a0e147ea428366e52e7f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    데이터는 행 단위로 움직인다.
        한 줄이 회원 한명
        한 줄이 게시판 하나


---