# 자료형 (Data type)
작성일시: 2021년 10월 5일 오후 4:04

## Intro

javascript는 연산 능력이 있다.

 예시) `1 + 2 = 3`

Data Type (① 자료형) : 연산에 필요한 값들의 종류 /ex) 1 2 3<br/>
Operator (② 연산자) : 연산 기호들의 의미 /ex) + =

위 요소를 가지고서 (③ 문법, 문장, 표현식)을 작성한다.

---

## 자료형 (Data Type)

> **상수 (값이 정해져 있는 형식)**
>
1. 정수 (number object)<br/>
: 음수, 소수를 제외한 양의 실수
2. 실수 (number object)<br/>
: 실제 사용 가능한 모든 수
3. 문자형 상수 (string object)<br/>
: " text "
4. 불린(boolean)<br/>
: true (1) / false (0)
5. null<br/>
: 값이 없다. (비어있다 X)

<br/>

> **변수 (변할 수 있는 값)**<br/>
-값을 저장하는 장소나 이름

  ex)  `a = 1`<br/>
        : (해석) 1을 a에 저장한다.<br/>
          여기서 a의 역할 -> 저장하는 장소 -> **변수

#### 재선언 vs 재할당
```jsx
var a = 1;
.
.
.
var a = 1;         <-- 재선언
.
a = 2              <-- 재할당
```

<br/>

### 변수 선언문 3가지

1. **var :** 변수 재선언(o) / 변수 재할당(o)     ,생략가능

    ```jsx
    var a=1;
    var a=1;
    a=2

    document.write(a);
    document.write(a);
    window.alert(a);
    ```

2. **let :** 변수 재선언(x) / 변수 재할당(o)

    ```jsx
    let a=1;
    let a=1;            <-- Error🔴
    a=2

    document.write(a);
    document.write(a);
    window.alert(a);
    ```

3. **const :** 변수 재선언(x) / 변수 재할당(x)

    ```jsx
    const a=1;
    const a=1;           <-- Error🔴
    a=2                  <-- Error🔴

    document.write(a);
    document.write(a);
    window.alert(a);
    ```
<br/>

### 변수 이름 규칙

일반적으로 변수 이름은 지정된 것이 아닌 만들어서 사용하지만, 규칙이 필요함.

> **이름규칙**

1. 알파벳, 숫자 사용가능
2. 한글, 특수문자, 공백 사용불가
3. 첫번째 글자는 _ 또는 알파벳만 가능 (특수문자 _ 사용 가능)
4. 대소문자 반드시 구분
5. 예약어 사용 불가

⭐변수의 이름만 보고도 용도나 기능을 예상할 수 있게 네이밍하기