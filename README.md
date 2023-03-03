* 타입스크립트: 자바스크립트를 한단계 끌어올린 언어, 자바스크립트 언어를 사용해 새로운 기능과 장점을 추가하는 언어
* 타입스크립트는 브라우저와 같은 자바스크립트 환경해서 실행할 수 없음 , node,js 에서 또한 타입스크립트를 실행할 수 없음, 자바스크립트를 실행할 수 있는 환경에서는 타입스크립트가 지원되지 않기 때문
* 타입스크립트는 프로그래밍언어이면서 도구인데 코드를 실행해서 타입스크립트 코드를 자바스크립트로 컴파일하는 컴파일러이다
* 타입스크립트는 중요한 작업을 수행하는데 타입을 추가하고 자바스크립트 언어 추가 기능에 기능을 추가하는데 이기능은 자바스크립트가 실행되고 브라우저 런타임에서 에러가 발생하기 전에 코드의 애러를 개발자가 미리 식별할수 있는 기회를 제공한다
* 바벨이라는것을 이용해서 구형 브라우저에도 동작하게 해줄 수 있다.
* 웹팩: 근래의 프론트엔드 웹개발에서 사용하는 구축도구로서 타입스크립트와 함께 사용하면 더 나은 프로젝트 설정이 가능해지며 이 도구를 사용하여 특정 작업을 더쉽게 한다 즉 훌륭한 개발경험과 최종 사용자에게 정말 적합한 코드를 최대한 활용할 수 있다.
  *  최신 프론트엔드 프레임워크에서 가장많이 사용되는 모듈 번들러
  *  모듈번들러: 웹 애플리케이션을 구성하는 자원(HTML, Javascript, images 등)을 모두 각각의 모듈로 보고 이를 조합해서 병합된 하나의 결과물을 만드는 도구를 의미, 
  *  모듈: 프로그래밍관점에서 특정 기능을 갖는 작은 코드단위 ex) 함수 모음 파일
  *  웹팩에서의 모듈: 자바스크립트에 국한되지 않고 웹 애플리케이션을 구성하는 모든 자원을 의미
  *  모듈번들링: 몇백개의 자원들을 하나의 파일로 병합 및 압축해주는 동작
* 폴리필: babel을 사용할때 ES6 를 ES5로 바꾸어 주지만 ES6의 Map, Promise, SEt 등등은 존재하지 않아서 번역을 해주지 못하는데 폴리필을 사용하면 사용가능
  * 브라우저에서 지원하지 않는 코드를 사용가능한 코드 조각이나 플러그인(추가기능)을 의미
* 타입스크립트는 함수 리턴값이 있어도 되고 없어도 되는건가?
* 타입스크립트 오브젝트 타입 사용법
```
const person: {
    name:String;
    age:number;
    
} = {
    name: 'asdf',
    age:30
}

//
그냥 밑의 방식으로 사용해도 된다

const person = {
    name: 'asdf',
    age:30
}
```
* any타입은 아주 유연하지만 유연성은 모든장점, 타입, 좋은 기능들을 활용하지 못하게 할수 있다.

* array타입 데이터 꺼내오는법
```
 hobbies :[1,2,3,4];

 for(const a of hobbies) {

 }
```
* tuple: 길이가 고정된 배열 -> 근데 지정된 인덱스 값마다 타입지정가능 -> 근데 push 메서드를 사용하면 문제 없이 배열의 길이가 늘어난다 -> 이게 튜플규칙을 무시하는 문제점이 있긴하다
```
role: [number, string];
```
* enum: 작성자가 나중에 코드를 봤을때 '1', '2' 이런식으로 되어있으면 다시찾기 어렵기 대문에 enum으로 개발자가 알아보기 쉽게하는게 좋음, 첫번째값의 기본값은 0인데 값을 할당가능도함
```
enum Role {
  ADMIN: 100,
  READ_ONLY, AUTHOR
}
```
* Any타입: Any는 어떤 값이나 종류의 데이터가 어디에 저장될지 전혀 알 수 없는경우에 대비하거나, 런타임 검사를 수행하는 경우 런타임 도중 특정 값에 수행하고자 하는 작업의 범위를 좁히기 위해 any를 사용하면된다, 그외는 쓰지 않는편이 좋음
* 여러가지 타입 쓰는법
  ```
  function a(input1: number| string, resultConversion === 'as-number' | 'as-string'){
    if(typeof input1 === 'number'){

    }
  }
  ```
  * 유니온 타입: 
  ```
  type Combinable = number | string;
  type ConversionDescriptor = 'as-nubmer' | 'as-text';
  ```
* 타입 얼라이어스:
```
  // 타입 앨리어스
type Person = {
  name: string,
  age?: number
}

```
* 페이지 들어왔을때 웹인지, 모바일인지 확인하는 코드
```
//모바일이면 true 반환
export const isMobile = () => {
  return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)
}
```
* 함수 리턴타임
```
function add(n1: number, n2:number): number {
  return n1 + n2;

}
```
* undefined 는 타입스크립트에서는 타입이다 -> 실제 값을 반환 하지 않을 때 사용 -> 매우 드문경우 사용
```
function add(n1: number, n2:number): undefined {
  return;

}
```
* 일반적으로 반환값이 없을때는 void 사용

```
let a: Function; //이렇게 하면 리턴값이 없으면 오류남
let a: () => number; //이렇게 함수형으로 바꾸면 됨

```
* 함수만 받을 수 있음
* 리턴값이 never: 리턴타입이 never가 사용되는 경우 항상 오류를 출력하거나 리턴값을 절대로 보내지 않음을 의미
* tsc init --명령어 치고 그다음부터 tsc 누르면 자동으로 js파일 생성됨
* tsc -w 사용하면 관찰모드로 들어가서 변경사항을 저장하면 자동으로 반영
* tsconfig.json에 exclude를 사용하면 컴파일 해서는 안되는 파일을 제외시킬 수 있다
* 타입스크립트 코드를 작성할때는 반드시 브라우저를 위해서 작성하는게 아님을 염두해 두어야한다
* 타입스크립트로 node.js 애플리케이션을 작성할 수도있는데 브라우저에서 잘작성되는 이유는 lib설정을 해서그럼 tsconfig.json
* tsconfig.json 에서 주석처리되있는거는 그거는 기본으로 설정하겠다는뜻 -> 주석을 풀면 내가 직접 설정을 해줘야함
* tsconfig.json sourceMap: 디버깅작업과 개발에 유용, true로 두면 source에 타입스크립트도 올라가는데, 브레이크 포인트를 두면 그 코드를 지나갈때 정지 하는데 아주 편리한 기능, 이 기능은 디버깅 프로세스를 한단계 향상시켜준다
* noEmitOnError: 타입스크립트에 문제가 있ㄴ느경우 true를 넣으면 문제가 되는 파일이 다시 생성되지 않음 -> 타입스크립트 파일에 에러가 있는 경우 자바스크립트 파일을 가져오고 싶지 않은 경우에 설정
* var를 안쓰고 let를 사용하는이유: 하위 범위내에서만 그 변수를 사용하고싶기 때문
* 나머지 매개변수 사용법
```
const add = (...numbers: number[]) => {
  return numbers.reduce((curResult, curValue) => {
    return curResult + curValue;
  }, 0);
}

const addedNumbers = add(5,10,2,3.7);

//튜플로 지정하고 싶을떄
const add = (...numbers: number[number, number, number]) => {
  return numbers.reduce((curResult, curValue) => {
    return curResult + curValue;
  }, 0);
}

const addedNumbers = add(5,10,2);
```
* 타입스크립트는 타입스크립트에서 일반 자바스크립트에 이르기 까지 코드를 컴파일할뿐만 아니라 최신 자바스크립트에서 이전 자바스크립트까지도 작업 수행을 지시하면 컴파일을 수행한다 es5로 놓으면 알아커 js 구문을 만든다
* 배열 디스트럭쳐
```

  let a = ['a','b','c'];
  [c,d, ...나머지] = a;
  
```
* 클래스
```
class A{
  name:string;

  constructor(n: string) { //초기화작업
    this.name = n;

  }
}

let b = new a('AAA');

```
```
class A {
  name: String;
  constructor(n: stirng){
    this.name = n;
  }
  describe() {
    console.log('a' + this.name);
  }
}

const accounting = new Department('Acconting');

accounting.describe(); //aAccounting

const b = {describe.describe};
b.describe(); //undefined 이 나오는데 그이유가  객체리터럴로 생성되기 때문, 클래스나 정의된 특정 클래스를 기반으로 하지 않고 더미객체로 생성되기때문이다. 사실상 describe로 함수자체를 전달

//그래서 describe 를 변경해야함
describe(this: A){
  console.log('a' + this.name);
}

const b = {name:'s', describe.describe}; 
b.describe(); //as 가 찍힘
```
* 클래스에서 필드에 뭐 안써있으면 public가 기본
* 생성자 받을 때 접근제한자를 지정해줄 수 있음
```
constructor(pricate id: string, public n: string){

}
```
* readonly: 데이터가 변경되는것을 막으려고 할때 사용, 자바스크립트에는 없는 기능
* proteced: 이클래스에서뿐 아니라 이클래스를 확장하는 모든클래스에서 사용가능, 접근은 가능한데 외부에서 변경불가능.
* private 쓸때는 getter, setter 사용하면됨
* get 사용할때는 메소드로서가 아닌 일반 속성으로 접근해야함
```
class A{
  private a: string;

  get getA() {
    if(this.a){
      return this.a;
    }
    throw new Error('no report found');
  }
  set setA(value :string) {
    this.a = value;
  }
}
let b = A();

b.setA('ccc');
var c = b.getA;

```
* get, set 는 로직을 캡슐화하는데 유용하다
* 정적메소드: 인스턴스를 만들지 않고 사용할수 있는 메소드
* 클래스 안에 함수가 있을 때 클래스를 인스턴스화 하지 않고 접근할수 있는 정적 메소드로 만들려면 static 을 앞에 붙여주면 정적으로 사용가능
* 