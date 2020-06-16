# Typescript

### 카테고리

#### variables

 - var(es5), let(es6), const(es6)가 있다.

##### scope 범위

 - var는 함수 단위로 scope가 적용
 
 - let, const는 블록 단위로 scope가 적용 된다.

##### var

 - 함수 단위로 적용. 함수 바깥에서는 접근할 수 없다.

        function outer() {
            function inner() {
                var score = 0;
            }
            inner();
            // console.log(score); // 사용 불가능 (score는 inner 함수 안에 있으므로)
        }

        function outer2() {
            if (true) {
                var score = 0;
            }
            console.log(score); // 함수 단위이기 때문에 접근 가능!
            for (var i = 0; i < 3; i++) {
                setTimeout(function() {
                    console.log(i); // i는 3이 계속 나옴 함수 단위로 부여가 되기때문에 100ms 이후에는 이미 갱신 되어져 있음.
                }, 100);
                
            }
        }
        outer2(); // 기대 동작과 매우 다르게 동작

        /* 결과값 : 0, 3,3,3 => 함수 단위로 var i가 부여되기 떄문에 루프를 다 돌고나서 진행되었다.*/ 

##### let, const

 - 블록 단위로 적용. 블록 바깥에서는 알 수 없다.
 
 - let 선언 시에 블록 scope 확인을 해줌. 값이 할당될 시에 타입이 자동으로 지정됨.(ex. number, string...)

 - let은 선언 시에 값을 반드시 할당할 필요가 없지만 const는 상수이기 때문에 초기 값이 반드시 필요하다.

        function outer3() {
            if (true) {
                let score = 0; // let 선언 시 블록 scope 체크도 해줌.
                score = 30; // 숫자형이라는 걸 알고 있어서 문제 없음
                // score = "30"; // 문자형일 경우 오류 발생. 값의 타입으로 타입이 지정됨.
                let score2; // 값이 지정되지 않는 경우 : any 타입으로 지정.
                score2 = 30;
                score2 = "30"; // 문자형도 문제가 없음 any 타입이라서
                // if type 지정을 원하면 지정할 수 있음.
                let type: number; // type이라는 변수가 number로 설정됨.
            }
            // console.log(score); // 블록 단위라서 불가능!
            for (let i = 0; i < 3; i++) {
                setTimeout(function() {
                    console.log(i); // 블록 단위로 적용 0, 1, 2 됨.
                }, 100);
                
            }
        }
        outer3(); // 기대 동작과 매우 다르게 동작

        function outer4() {
            if (true) {
                const score = 100; // const == 상수, 한번 정해지면 변하지 않는 값. 초기값이 무조건 채워져 있어야 함.
                // score = 30; // 새로운 값 재할당 불가.
            }
            // console.log(score); // 블록 단위라서 불가능!
        }
        outer4(); // 기대 동작과 매우 다르게 동작

#### types

##### 일반 타입

        let numValue: number;
        let stringValue: string;
        let boolenValue: boolean;
        let undefinedValue: undefined;
        let nullValue: null;
        let objValue: object;
        let symbolValue: symbol;

 - 위와 같은 형태의 type들이 존재.

 - 처음 숫자 타입이 입력되었을 때 (ex. numValue = 3) "3"과 같이 string 형태가 들어오면 에러가 난다.

 - null, undefined는 모든 타입의 **하위타입**이라서 상위타입(number, string, boolean....)에 적용이 가능하다. (ex. numValue = null)

 - any는 모든 타입의 **상위타입** 이라서 모든 하위타입을 받아들인다.

##### 배열 타입

        let nameList: string[]; // 선언
        nameList = []; // 빈 배열 또는 값을 채워서 넣어도 가능하다.

        let user1: { name: string, score: number}; // type을 inline으로 바로 정의가 가능.
        user1 = {
            name: 'j',
            score: 30
        }

        let tuple1: [number, string] // 첫번째 배열요소로 number, 두번째로 string을 받는다.
