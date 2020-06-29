
interface  Props {
  name: string;
  [key: string]: string; // 파라메터 (key 옆 타입은) string or number 만 올 수 있다. key number 일 경우 string 절대 못 옴
}

const p: Props = {
  name: 'hihi',
  a: 'd',
  b: 'e',
  c: '13',
};

let keys: keyof Props;

interface User {
  name: String;
  age: number;
  hello(msg: string): void;
}

let keysOfUser: keyof User;
// keysOfUser = 'bbb';

let helloMethod: User['hello'];
// helloMethod = function (msg: number) {
//
// }