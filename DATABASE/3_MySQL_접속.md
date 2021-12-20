# MySQL 접속
작성일시: 2021년 11월 18일 오후 2:55

## 폴더 위치확인

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/174e0752-4564-472f-bdc9-230fe0de4a81/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082327Z&X-Amz-Expires=86400&X-Amz-Signature=aa0cf0f32fb393b6116ecaeff6971b9363199beee83a6b14fa5ed6dd41c05be6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9aba1d31-07ef-444f-ab05-ca4d43dd84bd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082334Z&X-Amz-Expires=86400&X-Amz-Signature=b69e608c3fce8a9ff63244dfdd75b2a921950446539567882b649cd3f8444072&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

`xampp` 폴더에서 `mysql > bin > mysql.exe`가 있다.

**cmd창**에서 접속한다.

---

## MySQL 접속

1. **`Win + R` 열고 cmd 입력**

2. **cmd에서 폴더 이동하기**
cd : change directory ⇒ 폴더 이동
dir : 폴더 내용 보기
cd .. : 한 폴더 밖으로

`cd c:\xampp\mysql\bin` 으로 이동가능

3. **MySQL 로그인하기**

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/40383b0f-4e00-4444-a981-3f6474405259/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082343Z&X-Amz-Expires=86400&X-Amz-Signature=6b11ff3aff7846f2365b618598add7f4b15c1f380315ab9493b7c44928d81956&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    호스트는[`localhost`](http://localhost) 이고, localhost일 때는 작성 생략 가능하다.
    `loclahost`는`roof back address :**127.0.0.1`** 이다.

    사용자는 리눅스에서 root로 표현한다.

    비밀번호는 `-p`와 붙여서 작성한다. `root` 권한의 초기 비밀번호는 없으므로 작성 생략한다.

    ![Welcome이 나오면 접속 성공](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cee4a817-2d75-41b5-b6e3-425fc927284b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082350Z&X-Amz-Expires=86400&X-Amz-Signature=7103eb05d4bfff07b1986564f8d316fe58537ca19d9c4260193ac1b3e2cbb21a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    Welcome이 나오면 접속 성공

    실무에서 비밀번호 입력 시 `-p`까지만 작성하고*`enter`*를 누른다.

    ![비밀번호가 노출이 되지 않는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7a3a668e-5049-495f-9d89-4a36a715dc21/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082420Z&X-Amz-Expires=86400&X-Amz-Signature=0fdfe99eba1f22136d72df8b72d41173b696eab553c650b19cb90e54fd55e445&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    비밀번호가 노출이 되지 않는다.

4. **MariaDB 명령어 사용**
명령어의 끝은 `세미콜론 ;` 를 붙여서 종결은 나타낸다.

    <aside>
    💡 **databases;  tables;**  주의

    </aside>

    > 데이터베이스를 포함한 오브젝트 확인하기
    `show 오브젝트 이름`
    >

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b1c1207b-24f2-4ef6-ac3d-2b0fe5491040/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082457Z&X-Amz-Expires=86400&X-Amz-Signature=8b21370d917d7d4bd7f886c7f7e09c11cabb107e87afe413b939f6633850dc6e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    > 데이터베이스 목록 중 사용할 데이터베이스 선택하기
    >
    >
    > `use 데이터베이스 이름`
    >

    > 데이터베이스 내 테이블 확인하기
    >
    >
    > `show tables;`
    >

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/21c8927d-731a-415d-ae30-0dd321006f66/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082508Z&X-Amz-Expires=86400&X-Amz-Signature=da0a3717b1bf9f664a6e38a7f355f20fd3f79c8e7a512feb6b678bc40cf01c58&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


5. **DB 종료하기**
`exit` 또는 `quit` 입력

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f037c269-ab81-4f39-bd20-f44635f98c9b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082515Z&X-Amz-Expires=86400&X-Amz-Signature=4e7d66be6cb0489d5da1cddc13b6eace9d67de334294f2d1a0552b8b95d33da4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


---