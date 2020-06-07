# TIL

## Today I learned

 배운 내용을 정리 하는 레포

### 카테고리
#### Javascirpt Baisc
[함수](#함수)
#### Javascript
[프로토타입](#프로토타입)

#### 함수
 - 함수는 Javascript의 기본적인 블록 구성법이다. 
 - 함수는 task들을 실행하고 value를 계산한다.
 
#### 프로토타입

 - **prototype** 과 **\_\_proto\_\_** 의 차이  
    
        프로토타입(prototype)은 new 생성자로 생성 시
        프로토(__proto__)를 생성하는데 사용되는 객체다.

        프로토(__proto__)는 메서드를 사용 가능하게 하는 
        체인을 사용하는 실제 객체다.

 - **프로토타입(prototype)**은, **클래스 원형을 확장**할 때 쓰이고 **프로토(proto)**는 **해당 클래스에서 파생된 객체**에 **담기는 정보**다.

 - 프로토타입 체이닝을 통해 Object.prototype을 찾을 때 까지 \_\_proto\_\_ 객체는 \_\_proto\_\_ 안 \_\_proto\_\_ 를 다시 찾아간다.
