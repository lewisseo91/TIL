# Typescript

### 카테고리

#### Typescript 설정 (configuration)

 - tsc <fileName.ts> 의 명령어로 javascript 로 컴파일 가능하다.

##### --target

 - target 없이 컴파일하면 let, const 와 같은 es6 문법들은 var (es5이하)로 변환되어 나온다.

 - typescript에서 es6로 컴파일 하기위해서는 **tsc <fileName.ts> --target es6**를 지정해 준다.

##### --lib

 - promise와 같은 컴파일 시 변환 불가능한 것이 들어가면 오류가 난다. 

 - 이 때, 컴파일러에게 '이것은 es2015로 변환 시켜주시오.' 라고 알려줘야 하는데 이것이 --lib다.

 - **tsc <fileName.ts> --lib es2015,es5** 와 같은 명령어로 알려준다.

##### import

 - export default function <functionName> 을 통해 function 을 기본으로 사용가능하게 해주면 다른 파일에서도 import가 가능해진다.

 - import 했을 경우 그냥 컴파일하면 require 와 같은 문법이 사용되고 이를 import 로 바꿔주려면 target을 es6로 바꾸어주면 된다.

##### --showConfig

 - showConfig를 입력하면 configuration 구조가 어떻게 진행되는 지 보여준다.

 - **tsc <fileName.ts> --showConfig**와 같은 명령어를 입력해 확인한다.

##### tsconfig.json

 - typescript를 명령어로 계속 쭉 늘려서 **ex) tsc <fileName.ts> --target es6 --config es5,es2015,dom,es2016...** 같이 쓰는 것보다  
   tsconfig.json을 최상단에 위치시키고 tsc 명령어를 눌렀을 때 자동으로 configuration이 작동되게 하는 것이 좋다.

 - 객체 형태로 저장 -> {} 한다.

 - include : 컴파일할 폴더 위치, exclude : 제외할 폴더 위치(node의 경우 node_modules), compilerOptions : 컴파일 시 고려사항

##### compilerOptions

 - 컴파일 시에 해당 부분의 옵션들을 고려한다.

 - module : "commonjs", "es6" .... (적용할 모듈)

 - rootDir : 루트 폴더 위치

 - outDir : 주소로 사용할 폴더 위치

 - sourceMap : **true**일 때, 원래 ts파일구성을 볼 수 있다.

 - removeComments : **true**일 때, 컴파일 시 주석을 다 없애고 올려준다.

 - noImplicitAny : **true**일 때, argument로 들어가거나 type이 필요한 요소들에서 <any> 타입이 있을 경우에 오류로 나오게 한다.
