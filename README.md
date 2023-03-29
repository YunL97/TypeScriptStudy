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
* 정적속성도 마찾가지로 앞에 static로 해놓으면 인스턴스화 시키지 않고 접근가능 -> 정적속성은 인스턴스에서 유효하지 않은 인스턴스화 해서 메소드로 접근 불가능, this로 접근불가능 -> this는 클래스를 기반으로 생성된 인스턴스를 참조하기 때문 -> 그래서 클래스 내에 그냥 클래스 이름 박고 사용하면 될듯
*  추상클래스: abstract 를 가지고 있는 메소드가 있으면 클래스에도 abstract를 붙여야한다. 그럼 이 클래스를 상속받은 클래스는 재정의를 해줘야한다
*  추상메소드: 이 메소드의 형태와 메소드의 구조가 어떤것인지를 정의만 하고있을 뿐 그 외에는 아무것도 정의x
*  싱글톤 사용법: privatestatic instance: 클래스이름 쓰고
```
class 클래스이름{
 public static getInstance() {
  if(!클래스이름.instance){
    클래스이름.instance = new 클래스이름();
  }
  return 클래스이름.instance;
 }
}
 ```
 * 인터페이스: 객체의 구조를 설명,사용자 정의 타입으로 사용할뿐, 이 구조를 가져야하는 객체에 대한 타입을 확인하는 타입으로 사용가능
```
interface A {
  name:string;
  age: number;

  greet(b: string): void;
}

let user1: A;

user1 = {
  name: 'a',
  age: 30,
  greet(b: string){
    console.log('asdf);
  }
};

```
* 타입과 인터페이스 차이점: 인터페이스는 객체의 구조를 설명하기 위해서만 사용, 
* 인터페이스를 자주 사용하는 이유는 클래슥다 인터페이스를 이행하고 준수해야하는 약속처럼 사용할 수 있기 때문
* 클래스 사용할때
```
class A implements B,C {

}
```
* 읽기전용 인터페이스: 한번 설정되면 이후에는 읽기전용으로 설정, 객체가 초기화되면 변경x
* 인터페이스에 상속도 쓸 수 있음
```
interface A entends B {

}
```
* 인터페이스는 타입스크립트에만 있는 기능으로 자바스크립트에서는 찾아볼 수 없음 -> 컴파일 도중 코드를 검사하는데만 사용된 다음에 무시된다, output에 해당하는것은 아무것도 없음
* 타입 결합하는법
```
type A = {
  name: string;
};
type B = {
  name2: string;
};
type C = A & B; 

```
* 타입안에 속성 있는 지확인하는법
```
if('속성이름' in 타입이름){

}
```
* instanceof(타입가드): 객체를 기반으로 만들어진 함수로 확인가능 -> 클래스대신 인터페이스를 사용하면 구현이 불가능 -> 타입가드는 런타임시 얻은 정확한 타입을 기반으로 하는 한가지 또는 다른 기능을 수행하는 코드를 작성할 수 있게 된다.
```
const v1 = new Truck();

function A()vehicle: Truck) {
  if(vehicle instanceof Truck){
    vehicle.함수;    
  }
}
```
* 인터페이스는 어떤 자바스크립트 코드와도 비교할 수 없음
* union: typeof 타입가드나 타입가드를 도와준다 -> 타입가드를 쉽게 구현할수 있게 해주는 타입, 유니온은 해당 속성을 설명, switch 문을 사용하면 타입스크립트에서 자동완성을 시켜주기 때문에 오타입력을 없애준다
```
interface Bird{
  type: 'bird' // 이게 유니온
}
```
* 리터럴: 데이터 그자체를 의미
* 형변환: 타입스크립트가 직접 감지하지 못하는 특정 타입의 값을 타입스크립트에 알려주는 역할을 한다. 
```
var a = <HTMLInputElement>document.getElementById('id네임');
a.value = 'asd';
//or 위아래가 같음
var a = <HTMLInputElement>document.getElementById('id네임') as HTMLInputElement;
```
* 느낌표: null을 반환하지 않을것이라는 확신이 들때 사용, 아니면 if문사용하면됨
```
if(a){
  (a as HTMLInputElement).value = 'asd';
}
```
* 인덱스 속성: 인터페이스 같은거 구조짤때 사용하는듯?
```
interface ErrorContainer {
  [prop: string]: string;
}

const errorBag: ErrorConatiner = {
  email: 'not a valid email'
}
```
* 함수오버로드: 동일한 함수에 대해 여러 함수 시그니처를 정의할 수 있는 기능 => 다양한 매개변수를 지닌 함수를 호출하는 여러가지 가능한 방법을 사용해서 함수 내에서 작업을 수행할 수 있게해준다. -> 리턴타입 확실하게 적용해 줄 수 있음
```
function add(n: number): string;
function add(a: number, b: number): number;
function add(a: number|string, b: number|boolean) {

}
```
* 옵셔널 체이닝: 데이터를 가져오지 못하는경우를 대비가능, 데이터가 들어있지않으면 undefined 반환, 함수호출에도 사용가능
```
const result = user?.getName?.();
```
* null 병합: ?? 앞의 값이 null이나 undefined면 'asd' 로 값을 넣어준다
```
const a = null ?? 'asd';
```
* 제네릭: 제네릭 타입 정보를 사용하면 보다 나은 타입 안정성 확보가능, 구체적인 타입이 아니기 때문에 어떤 객체든 입력할 수 있어서 타입스크립트가 두 객체의 인터섹션이 반환 된다는것을 추론가능
```
function a<T, U>(oba: T, obb: U): T & U  {
  ruturn Object.assign(oba, obb);
}
```
* 제네릭타입 제약 주는법: 
```
function a<T extends pbject, U>(oba: T, obb: U): T & U  {
  ruturn Object.assign(oba, obb);
}
```
* Lengthy: 타입스크립트에서 사용되는 유니온타입중 하나, length프로퍼티가 있는 타입을 의미
* keyof: 인터페이스나 타입의 속성 이름들을 유니온 타입으로 반환, 해당 타입으 속성 이름을 추출하거나 타입안에서 해당속성을 참조 가능
```
function a<T extends object, U extends keyof T>(obj: T, key: U){
  return 'value: ' + obj[key];
}

a({name: 'a', 'name'});
```
* 제네릭 클래스: 공통 클래스를 마들 때 사용, 근데 객체 같은거 넣으면 참조타입이기때문에 내가 생각한것과 드르게 결과가 나올 수있다.
```
class A<T extends string | number | boolean>{
  private date: T[] = [];
}

const b = new A<string>();

```
* 제네릭 타입은 작업을 쉽게 수행할 수 있게 해주며 완벽한 유연성의 조화를 제공
* Partial: 인터페이스 Partial<인터페이스이름> 써주면 다 옵셔널로 바뀜
* 유니온 타입은 모든 메소드 호출이나 모든 함수 호출마다 다른 타입을 지정하고자 하는경우에 유용
* 제네릭 타입은 한타입으로 고정
* 데코레이터 : 제네릭보다 상급인 특성
```
function Logger(constructor: Function){
  console.log('logging');
  console.log(construecor);
}

@Logger
class A{
  name="a";

  constructor() {
    console.log('b');
  }
}

const a = new A();
//결과
logging
class A{
  name="a";

  constructor() {
    console.log('b');
  }
}
b
```
*  데코레이터 팩토리: 데코레이터함수를 반환하는 함수, 클래스, 메서드, 속성등의 데코레이션 대상에 적용되는함수
```
function myDecoratorFactory(message: string) {
  return function(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    console.log(message);
    return descriptor;
  }
}

class MyClass {
  @myDecoratorFactory('Hello, world!')
  myMethod() {
    // ...
  }
}
```
* 데코레이터는 밑에서 위로 실행: B 실행, A실행
```
@A()
@B()
class C {

}
```
* 속성 데코레이터: 
```
function Log(target: any, propertyName: string | Symbol){
  console.log('a')
  console.log(target, propertyNAme)
}
class A{
@Log
title: string
}
//결과 
//a
//{constructor: f, getPriceWithTax: f}  " title"
```
* addEventListener 같은거 사용할 때 클래스 안에있는 this를 불러올라고하면 undefined를 가져오기 때문에 bind로 묶어야한다
```
const p = new Printer();
const button = document.querySelector('button')!;
button.addEventListener('click', p.showMessage.bind(p));
```
* !! 비-널연산자: 데이터를  boolean으로 바꿀때 사용
```
var a = "test";	      //a: "test" (조건문 적용시 true)
var b = !"test";      //b: false
var c = !!"test";     //c: true
```
* 사용자정의 타입을 사용하면 타이핑을 향상시킬 수 있다.
* 모듈: 모듈형식의 코드를 작성해서 여러개의 파일에 코드를 나누고 각 파일이 관리가능하고 유지보수 가능하게 하는게 좋음
* 코드를 여러개의 파일로 나누기위한방법
  * 1. 여러개의 코드파일, 여러개의 타입스크립트파일과 폴더를 작성하고 모든 코드파일을 자동으로 소스디렉토리에 컴파일한 후 수동으로 컴파일 된자바스크립트를 html에 임포트 하는것 -> 좋은방법x
  * 2. 네임스페이스, 파일번들링: 서로 임포트해서 내가 관리할 임포트가 줄어들게 되고 html 파일 내에 서로다른 임포트들을 수동으로 관리할 필요가 없어짐 -> 제작을 위해 하나의 파일만을 전송해야하기 때문에 웹팩가 같은 서드파티 툴이 필요하다. 

*  네임스페이스: 그냥 고유한 식별자를 생성하기 위한 일종의 접두사라고 생각하면될듯 -> 포넌트의 이름충돌을 방지하기 위해 사용 => 코드 를 작업할 때 찾고자 하는것을 신속히 찾을수 있고 다음 작업할 곳을 찾기위해 큰파일에서 스크롤을 움직이지 않아도 되는 작고 집중된파일로인해 훨씬 관리에 용이합니다.
```
export namespace CommonModel {
  export interface Common {
    errCode: string
    errMsg: string
  }
}

```
* ?? || 차이: ??는 오직 null, undefined만 체크, ||는 null, undefined, 0, false등등을 체크
* 웹팩: es6 모듈을 사용할때 코드관리가 용이해지는 반면에 이모듈을 다시 작업하게 하는 단점이 있는데 이를 해결하는것이 웹팩, 파일을 묶는것을 도와주는 도구
* 웹팩을 사용하지않으면 http요청의 양만으로 인해 다량의 대기시간이 발생하고 프로젝트가 느려질 수 있다.
* 웹팩은 묶고(bundling), 빌드하고(building), 종합(orchestration)하는 도구
* 웹팩을 사용할 때 mode: 'production' 으로 놓으면 최적화, 코드경량화등을 지시한다
* 현대 웹개발에서 일반적으로는 서드파티 라이버르리를 이용해서 개발을 한다
* 자바스크립트 라이브러리를 사용할때는 타입스크립트설정에서 noEmitOnerror을 false로 설정 => 타입스크립트가 이해를 하지 못하기 때문, 타입스크립트가 아닌 자바스크립트로 이루어진 라이브러리이기때문이다. @types/ 뒤에 패키지 이름이 오는방식인 패키지들은 검색되는 모든 서드파티 라이브러리들을 대상으로 기본적으로 존재
* declare: 타입스크립트로 작성하지 않은 코드의 타입정보를 컴파일러에게 알려주는 선언, 대게 외부 사용자에게 내가만든 라이브러리의 타입정보를 알려줄 목적으로 d.ts 파일을 정의할때사용

* 스프링의 어노테이션같은게 일반적으로 많구나 -> flutter jsonserializable패키지, 타입스크립트 데코레이터나 벨리데이터 같은거 다비슷하네
* event.stopPropagation(): 이벤트가 상위 dom으로 전파되지 않게하기 위해 사용
* d.ts파일: type을 정의(declare)하기위해 존재하는 파일, 기존 자바스크립트로 만들어진 서드파티 모듈들을 타입스크립트 환경에서도 사용할 수 있도록 따로 타입만 정리해서 넣어둔 파일 => 기존에는 js방식으로 돌아가던 라이브러리를 ts환경에서 사용하게 되는 경우 타입체킹이 필요한 타입들을 불러와야하기때문에 추가적인 타입선언 모듈을 받아서 동작시키는것
* script태그에서 defer: 백그라운드에서 js를 다운로드, => 지연 스크립트를 다운로드 하는 도중 html파싱이 멈추지않음, 모든 dom이 로드된 후에 실행, 스크립트 다운로드 백그라운드에서 하고 dom 로드다돼면 그제서야 실행
* script태그에서 async: 백그라운드에서 다운로드, async스크립트를 실행중일때는 html파싱이 멈춤, 실행순서 보장 x => dom에 접근하지않거나 다른 스크립트에 의존적이지 않은 스크립트들을 독립적으로 실행해야할때 효과적
*  서드파티라이브러리를 사용할때 타입스크립트와 사용할수 있는지 확인하고 존재하지 않는다면 타입패키지를 설치하면된다.
* 타입스크립트를 nodejs 에도 사용할 수 있음
* 타입스크립트를 넣고 실행을 해도 처리가되는데 파일안에 있는 내용을 단지 자바스크립트로 처리를한다. -> 설정을 해줘야함 -> ts-node라는 패키지를 설치 -> 근데 개발단계에서는 괜찮지만 프로덕션준비가 완료되면 이상적이지않음, 코드가 실행되는게 버겁기때문
* 