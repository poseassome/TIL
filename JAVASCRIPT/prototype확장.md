# 프로토타입 확장
(extends, 상속)<br/>
부모 => 확장 => 자식

클래스를 사용해도 된다.

```jsx
// super class (상위 프로토타입 생성)
function Animal(name, sound){
  this.name = name;
  this.sound = sound;
}

// 기능 부여
Animal.prototype.getInfo = function() {
  return (
    this.name + '가(이)' + this.sound + '  소리를 낸다.'
  );
}

// 만든 기능 상속
function Friends(name, sound){
  // Animal 생성자 함수의 기능 재활용
  // Animal 호출, 여기서 this는 생성될 instance
  Animal.call(this, name, sound);
}

const dog = new Friends('개', '멍멍');
const cat = new Friends('고양이', '야옹');

// 지금 상태로는 동작하지 않음. 프로토타입 연결 x => 확장해야한다.
dog.getInfo()     // dog.getInfo is not a function
```

```jsx
// super class (상위 프로토타입 생성)
function Animal(name, sound){
  this.name = name;
  this.sound = sound;
}

// 기능 부여
Animal.prototype.getInfo = function() {
  return (
    this.name + '가(이)' + this.sound + '  소리를 낸다.'
  );
}

// sub class
function Friends(name, sound){
  Animal.call(this, name, sound);
}

Friends.prototype = Object.create(Aniaml.prototype);
Friends.prototype.constructor = Friends;

const dog = new Friends('개', '멍멍');
const cat = new Friends('고양이', '야옹');


dog.getInfo();    // 개가(이) 멍멍 소리를 낸다.
cat.getInfo();    // 고양이가(이) 야옹 소리를 낸다.

dog.constructor.name    // Friends
```
super class를 sub class로 확장하였다.<br/>
sub class는 Animal 클래스로부터 파생된 클래스이다.

instanceof로 어디서부터 파생됐는지 확인가능하다.