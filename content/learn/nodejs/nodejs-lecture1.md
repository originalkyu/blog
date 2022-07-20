---
title: "Nodejs Lecture1"
date: 2022-07-17T11:58:36+09:00
type: 
draft: false
---

## Node.js 이해
* 웹 환경에서 사용자와 상호작용이 커지면서 고성능의 JavaScript가 필요해졌다. 그리고 V8 엔진이 등장으로 고성능 JavaScript를 실행할 수 있게 됐다.
* JavaScript를 브라우저 외부에서 사용하기 위한 목적으로 Node.js가 탄생했다.
* Node.js 는 자바스크립트를 어느 환경에서나 실행할 수 있게 해주는 실행기이다.
* 브라우저의 자바스크립트는 브라우저에서만 싱행되므로 웹 내부에서 제한된 동작만을 할 수 있다. 웹 프론트 개발자의 언어이다.
* Node.js는 다양한 플랫폼에서 실행할 수 있도록 한다. 제한 없는 동작을 가능하게 하고, 다양한 어플리케이션 개발을 할 수 있다.

## Node.js의 특징
* 싱글 쓰레드 - 비동기 - 이벤트 기반
* 싱글 쓰레드이므로 비동기 동작이 필요하고, 비동기 동작을 구현하기 위해 이벤트 기반의 동작 방식을 이용한다
#### 싱글 쓰레드
* 쓰레드란 명령을 실행하는 단위이다. 한 개의 쓰레드는 한 번에 한 가지 동작만 실행가능하다
* 쓰레드가 늘어나지 않기 때문에 리소스 관리에 효율적이지만 CPU 연산 작업처럼 쓰레드 기반의 작업들에는 효율이 떨어진다
* Node.js 는 비동기 동작으로 쓰레드 기반의 작업을 최소화
#### 비동기
* 동작을 실행한 후 완료가 되길 기다리지 않고 다른 동작을 바로 실행
#### 이벤트 기반
* 이벤트 기반이란 비동기 동작의 완료를 처리하는 방법이다.
* 비동기 방식은 특정 동작을 실행한 후, 해당 동작을 신경쓰지 않지만, 대신 해당 동작이 완료될 경우 실행할 함수를 미리 등록한다. 비동기 동작이 완료되면 미리 등록된 함수를 실행한다

## ES6
* ECMAScript 버전 6 이후를 통틀어 일반적으로 ES6라고 부른다. 현대적인 자바스크립트 문법이라고 생각하면 된다.
* ECMAScript는 계속해서 발전해나가는 JavaScript의 표준문법이다.
* Node.js는 최신 ECMAScript를 지원한다. 하지만 모든 문법을 지원하지는 않는다.

## 이벤트 루프
* Node.js가 비동기-이벤트 동작을 처리하는 일련의 반복 동작으로, 비동기 코딩이 어떤 순서로 수행되는지에 대해 이해할 수 있다.
* Call Stack, Message Queue, Job Queue로 구성되어 있다
* Call Stack에는 작성된 함수들이 등록되는 LIFO 스택이다. 이벤트 루프는 콜스택이 비어있을 때까지 스택의 함수를 실행한다
* Message Queue는 setTimeout 같은 지연실행 함수를 등록하는 FIFO큐이다. zhftmxordl qldjdlTdmf ruddn emdfhrehls gkatnfmf zhftmxordp cnrkgksek
* Job Queue는 Promise에 등록된 콜백을 등록하는 FIFO 큐이다. 콜스택이 비어있지 않더라도 상위함수가 종료되기 전에 잡큐에 등록된 콜백을 콜스택에 추가한다
* 즉, setTimeout 등의 함수는 콜스택이 비어있을 때 실행되고, Promise는 상위함수가 종료되기 전에 실행된다

---

## 실습

#### ES6 자주 사용되는 문법
```JS
// 1. var 대신 const, let을 이용한다
let variable = 1;
const constant = 2;

variable = 2;
//constant = 3;
    // error

console.log('variable', variable, 1);
console.log('constant', constant, 2);

//-----------------------------------

// 2. Template String 사용하기

// + 를 사용한 문자열
const animal = 'Cat';
const legs = 4;
const sound = 'meow';

const explain = animal 
    + ' has ' 
    + legs 
    + ' legs.\n' 
    + animal 
    + ' says \"' 
    + sound 
    + '\".';
    
console.log(explain);

// Template String 이용
const animal = 'Cat';
const legs = 4;
const sound = 'meow';

const explain = `${animal} has ${legs} legs.

${animal} says "${sound}".`;

console.log(explain);

//-----------------------------------

// 3. arrow function 사용하기
const add = (a, b) => {
    return `${a}+${b}=${a+b}`;
}

const add2 = (a, b) => (`${a}+${b}=${a+b}`);

module.exports = add;

//------------------------------------

// 4. ES6 class 사용하기
class Animal {
    constructor(name, sound) {
        /* constructor 완성하기 */
        this.name = name;
        this.sound = sound
    }
    
    explain() {
        console.log(`${this.name} says ${this.sound}`)
    }

    const cat = new Animal("cat", "mung");
}

// "duck", "quack"
const duck = new Animal("duck", "quack");

//------------------------------------

// 5. ES6 destructing 사용하기
// 쉽게 값을 꺼내올 수 있다

// object destructing
const duck = {
    name: "duck",
    sound:"quack",
};

// const name = duck.name;
// const sound = duck.sound;
const { name, sound } = duck;
const { name: aa, sound: bb } = duck;

console.log("name: ", name );
console.log("sound: ", sound);

console.log("name: ", aa );
console.log("sound: ", bb);


// array destructing
const animals = ["duck", "cat", "bear"];

//const first = animals[0];
//const second = animals[1];
//const third = animals[2];
const [first, second, third] = animals;


console.log("first: ", first);
console.log("second: ", second);
console.log("third: ", third);
```
* Template String을 사용할 때는 백틱(`)에 주의한다

#### callback 사용하기
```JS
function countDown(count, callback) {
    // count 출력
    console.log(count);

    // count가 0이라면 callback함수 호출 후 종료
    if ( count == 0 ) {
        callback();
        return;
    }


    // count가 0이 아니라면 재귀함수
    setTimeout(() => {
        countDown(count -1, callback);
    },1000);
    return;
}

countDown(5, () => {
    console.log("BOOM!");
});
```
* setTimeout(함수, 1000); 1000ms 이후에 함수 실행
* callback 함수를 인자로 가지는 함수는 내부에서 callback 함수를 실행한다
* 이벤트 함수를 인자로 전달해서 등록하는 형태이고, 이벤트를 비동기 동작으로 수행한다. 
* error와 결과를 같이 전달하는 것이 표준이다.
* 다음처럼 콜백 지옥에 빠질 수 있다.
```JS
db.getUsers((err, users) => { // callback1
    if (err) {
        ...
        return;
    }
    async1(users, (r1) => { // callback2
        async2(r1, (r2) => {
            async3(r2, (r3) => {
                ...
            })
        })
    })
})
```
* 1 getUsers이 실행되면서 생긴 err, users를 필요로하는 callback1이 전달되고 실행됨
* 2 callback1이 실행될 때 callback1 내부의 async1이 실행된다.
* 3 async1는 callback2를 인자로 가진다. 
* 4 callbakc2에는 async1이 실행될 때 생긴 r1이 전달된다
* 5 (2, 3, 4) 반복 
#### promise 의 작성과 사용
```JS
// callback으로 작성
function adder(a, b, callback) {
    if (a == 0 || b == 0) {
        callback("no zero", null);
        return;
    }
    console.log(`${a}+${b}=${a + b}`);
    
    callback(null, a + b);
}

function handle_error(error) {
    console.log("ERROR: ", error);
}

function add_all(a, b, c) {
    adder(a, b, (err, result) => {
        if (err == null) { // error 가 아니라면
            adder(result, c, (err, result2) => {
                if (err == null) {
                    console.log(`${a}+${b}+${c}=${result2}`);
                } else {
                    handle_error(err);
                }
            });
        } else {
            handle_error(err);
        }
    });
}
// adder(a,b, (err, result) => ...) 는 a+b하여 result를 만들어서 callback함수에 인자로 전달한다

// promise로 작성
function adder_promise(a, b) {
    return new Promise((resolve, reject) => {
        adder(a, b, (err, result) => {
            if (err) {
                /* 1. promise 에서 에러 처리하기 */
                reject(err);
                return;
            }
            /* 2. promise 에서 결과값 처리하기 */
            resolve(result);
        });
    });
}

function add_all_promise(a, b, c) {
    adder_promise(a, b) // promise 함수 실행
        /* 3. then 을 활용하여 result 와 c 를 add_promise 하기 */
        .then((result) => { // result는 adder_promise(a,b)의 결과. then에는 callback함수로 adder_promise(result, c)가 등록됨
            return adder_promise(result, c); // promise 함수 실행 2
        })
        // .then((result) => adder_promise(result, c)) 로 작성해도 된다
        .then(result2 => {
            console.log(`${a}+${b}+${c}=${result2}`);
        })
        /* 4. catch 를 활용하여 promise 의 에러를 handle_error 함수로 전달하기 */
        .catch((err) => handle_error(err));
        // .catch(handle_error); 로 작성해도 된다.
}


```
* Promise 함수는 Promise 객체를 반환한다
* Promise 객체는 resolve 함수와 reject 함수를 인자로 하는 함수를 가진다.
* resolve는 then에 등록된 callback을 실행하고, reject는 catch에 등록된 callback을 실행
* Promise 함수를 이용해서 callback함수를 보기 좋게 만든다
* Promise 함수의 동작이 완료되면 then에 등록된 callback 함수가 실행된다
* Chaining을 이용해서 코드를 간결하게 할 수 있다
* short-hand 표현 방법으로 return이나 인자가 하나인 경우 () 을 생략하여 코드를 간결하게 할 수 있다
* 오류가 발생하면 catch에 등록된 callback을 실행한다

#### async - await 사용하기
```JS
function adder_promise(a, b) {
    return new Promise((resolve, reject) => {
        resolve(a+b);
    });
}

function main_promise(a, b, c, d) {
    Promise.all([
        adder_promise(a, b),
        adder_promise(c, d),
    ])
    .then(([r1, r2]) => { // promise.all([]) 로 실행시켜서 r1, r2로 한번에 받고 있다.
        return adder_promise(r1, r2);
    })
    .then((r3) => { // adder_promise(r1, r2)의 결과를 r3로 전달받고 있다.
        console.log(`${a}+${b}+${c}+${d}=${r3}`);
    });
}

/* 1. main 을 async 함수로 선언 */
async function main(a, b, c, d) {
    /* 2. 두 promise 함수를 동시에 실행하여 결과를 r1, r2에 저장 */
    const [r1, r2] = await Promise.all([
        adder_promise(a, b),
        adder_promise(c, d),
    ])
    /*3. r1 과 r2 를 한번 더 adder_promise 로 실행 */
    const r3 = await adder_promise(r1, r2);
    console.log(`${a}+${b}+${c}+${d}=${r3}`);
}

main(1,2,3,4);

```
* async - await은 promise의 다른 문법이다
* async 함수 내에서 promise 함수의 결과는 await으로 받을 수 있다
* await 한 promise 함수가 완료될 때까지 다음 라인으로 넘어가지 않는다
* 순차적 프로그래밍처럼 작성할 수 있다.
* async 함수의 return은 Promise이다
* Promise.all([]) 은 promise 함수를 동시에 실행시키고 등록된 모든 함수가 마무리되면 결과값을 한꺼번에 반환한다