# 회원가입 페이지 구현(전체 PHP)
작성일시: 2021년 12월 3일 오후 5:32

## 회원가입 페이지 구현_insert.php

```php
<?php
// 입력받은 값 변수에 저장
	$u_name = $_POST["u_name"];
	$u_id = $_POST["u_id"];
	$pwd = $_POST["pwd"];
	$birth = $_POST["birth"];
	$postalCode = $_POST["postalCode"];
	$addr1 = $_POST["addr1"];
	$addr2 = $_POST["addr2"];
	$email = $_POST["email_id"]."@".$_POST["email_dns"];
	$mobile = $_POST["mobile"];
	$reg_date = date("Y-m-d");

// 값 확인 (동작 확인용이라 없어도 됨.)
	echo "이름 : ".$u_name."<br>";
	echo "아이디 : ".$u_id."<br>";
	echo "비밀번호 : ".$pwd."<br>";
	echo "생년월일 : ".$birth."<br>";
	echo "우편변호 : ".$postalCode."<br>";
	echo "기본주소 : ".$addr1."<br>";
	echo "상세주소 : ".$addr2."<br>";
	echo "이메일 : ".$email."<br>";
	echo "전화번호 : ".$mobile."<br>";
	echo "가입일 : ".$reg_date."<br>";

// DB 접속 및 문자셋 설정
	$dbcon = mysqli_connect("localhost", "root", "", "front") or die("접속에 실패하였습니다.");
	mysqli_set_charset($dbcon,"utf8");

// 쿼리문 작성
	$sql = "insert into members(";
	$sql .= "u_name, u_id, pwd, birth, postalCode, addr1, addr2, email, mobile, reg_date";
	$sql .= ") values(";
	$sql .= "'$u_name','$u_id', '$pwd', '$birth', '$postalCode', '$addr1', '$addr2', '$email', '$mobile', '$reg_date'";
	$sql .= ");";
	echo $sql;

// DB로 전송
	mysqli_query($dbcon, $sql);

// DB 접속 종료
	mysqli_close($dbcon);

// 결과 페이지 출력
	echo "
	  <script type=\"text/javascript\">
	    location.href=\"welcome.php\";
	  </script>
	";
?>
```

---