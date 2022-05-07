# Tailwind CSS
**utility** 우선 CSS 프레임워크
> utility는 tailwind가 많은 `classname`을 가지고 있다는 것을 의미한다.

각 `classname`을 조합해서 css를 적용한다. [Tailwind CSS](https://tailwindcss.com) <br/>
Bootstrap처럼 스타일이 정해져있지 않고 서로 다른 `classname`을 사용하여 다양한 스타일 적용이 가능하다. 

반응형 디자인 적용 또한 가능하다.
- *medium*, *large*, *x-large*, *2x-large*와 같이 화면 각각에 해당하는 `classname`을 제공함.
- ex) `lg:max-w-5xl lg:gap-x-20 lg:grid-cols-2` => large 화면에만 적용

## World-class IDE Integration
tailwind css는 무수히 많은 classname을 가진 큰 파일이다.<br/>
vscode extension에서 [**Tailwind CSS IntelliSense**](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)을 설치한다.
- 색상을 미리 볼 수도 있고, 자동완성 기능이 있다.
- `classname`에 마우스를 올리면 해당 class의 내용을 알 수 있다.