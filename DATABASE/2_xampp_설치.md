# xampp 설치
작성일시: 2021년 11월 18일 오전 11:51

# Intro

웹 프로그래밍을 하기 위해서는 환경 설정 3가지가 필요하다.

웹 서버 / 언어 / DBMS

웹 프로그래밍은 FTP로 올려서 웹 서버로 확인하는 과정이 무조건인데,
(트랙픽 고려해야함_트래픽 초과되면 그 날은 접속 불가)

개발 과정에서는 컴퓨터에 트래픽 제한 없는 서버를 사용하여 확인한다.

사용할 프로그래밍 언어는 php이므로,
php를 실행하기 위해서는 리눅스 운영체제가 필요하다.

하지만, 리눅스가 없으므로 대부분의 운영체제에서 사용가능한 Apache를 사용한다.

필요한 프로그램들은 묶어서 제공해주는 xampp를 설치한다.

---

## xampp 설치

1. 홈페이지 접속

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7fec5300-779e-48ad-a814-fa994f4a145d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082130Z&X-Amz-Expires=86400&X-Amz-Signature=2ff12f5f8d5991448d5c93e513f879caad433ce541e2600ff5a8c152b4cde5c5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


2. 다운로드 페이지 이동

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/12a9dcdc-9deb-4ffc-8742-49114823780b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082140Z&X-Amz-Expires=86400&X-Amz-Signature=089e11fa7e8ebce071a064420919cb53ae2878f0bdc3c3d67d7eb09b3c7bd2fe&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

3. 버전 선택하여 다운로드 하기 위해 이동

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f0745274-eb5e-4602-bcf1-b7c49a2e4091/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082148Z&X-Amz-Expires=86400&X-Amz-Signature=9426f00414e7407a0e8911d08ec3298ca69b8799a4485e3200220d74f7ea41bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


4. 버전선택(Windows)

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/175a1718-c12b-4ce9-84ba-527f9fb8ef39/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082210Z&X-Amz-Expires=86400&X-Amz-Signature=19dfaf7beb0e7c2898d6c869a02e1cb751729ab12388a57f6fcf0334937174a6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    ![실무에서는 아직 php 8버전 보다 7버전 많이 사용](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1af3db9e-8975-4751-b167-7358cd1be831/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082216Z&X-Amz-Expires=86400&X-Amz-Signature=8a79d88cd4099ae6d89d1841795e650470c5cac9efd1a142d155220ec0cfea2f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    실무에서는 아직 php 8버전 보다 7버전 많이 사용

    ![installer / Portable 중 Portable .zip 파일 다운로드
    ](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/94349464-5258-488a-b1ef-54b3c59ef588/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082226Z&X-Amz-Expires=86400&X-Amz-Signature=03d2d01f0a1684c4936963f935e291487b70b821e6854ad59239086736d79039&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    installer / Portable 중 Portable .zip 파일 다운로드

5. 받은 파일 압축풀기
6. 압축 푼 파일에 `xampp` 폴더는 C: 으로 이동한다.

7. 환경변수 설정

    ![아무 키 누르고 창 닫히면 끝 (환경변수 자동으로 설정)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b12292c7-66a1-4b67-b2a5-92688a6261a2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082242Z&X-Amz-Expires=86400&X-Amz-Signature=ba8d7bc3182b7d7368b7f63a22e624f4ce263cec36f7fb74d02f092b5f5ee04a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    아무 키 누르고 창 닫히면 끝 (환경변수 자동으로 설정)


8. 컨트롤러 실행

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c70fffeb-d014-4a38-bcbe-662e8c87fe43/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082250Z&X-Amz-Expires=86400&X-Amz-Signature=cb09bff39c0572d23ad7675666e4983e8fca8950b08f688344d4d1b8172673a0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    ![MySQL 'Start' 클릭하여 실행](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7e4396e8-765c-41f5-865c-62b1c00c3ba9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082301Z&X-Amz-Expires=86400&X-Amz-Signature=4021ff36baef8b332be3918f28a704a18cb80d533a43e4e4df88a82664732eca&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    MySQL 'Start' 클릭하여 실행


<aside>
💡 다른 AMP 프로그램이나 DB프로그램이 실행되고 있으면 충돌이 일어남.
기존 파일들 지우고 다시 설치해야 함. (같은 port 이용)

</aside>

---