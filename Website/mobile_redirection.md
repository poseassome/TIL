# mobile redirection
작성일시: 2022년 1월 10일 오전 10:58

PC용 웹 사이트와 모바일 웹 사이트를 별도로 운영할 시,
모바일 기기에서 PC 웹사이트 주소로 접속할 때 자동으로 모바일 웹 사이트로 이동하기로 한다.

ex) 네이버의 경우 PC 주소는 (http://www.naver.com)이고, 모바일 주소는 (http://m.naver.com)이다.

## 폴더 생성

모바일용와 PC용 웹사이트 모두 가지고 있을 폴더를 생성한다.
⇒ dothome에 업로드할 때 html 폴더 역할

- 📂**redirection**
    - 📂**web**

        📑index.html

    - 📂**mobile**

        📑index.html


## 모바일 웹 이동 script 코드 작성

```jsx
<script type="text/javascript">
	var mobileKeyWords = new Array('iPhone', 'iPod', 'BlackBerry', 'Android', 'Windows CE', 'LG', 'MOT', 'SAMSUNG', 'SonyEricsson');
	for (var word in mobileKeyWords){
	    if (navigator.userAgent.match(mobileKeyWords[word]) != null){
	        location.href = "이동할 모바일 주소";
	        break;
	    }
	}
</script>
```

해당 코드는 PC용 웹사이트파일에 작성한다.

## Dothome 업로드

dothome 계정의 html폴더에 **📂web, 📂mobile** 폴더를 업로드하고,
각각 PC와 모바일기기에서 PC 웹사이트 주소를 입력했을 때 보이는 화면을 확인한다.