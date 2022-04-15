#### promise any
https://dmitripavlutin.com/promise-any/

#### mdn promise
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

#### async 
https://eloquentjavascript.net/11_async.html

#### https://javascript.info/promise-basics

#### promisify
https://javascript.info/promisify

#### async await 
https://javascript.info/async-await

#### promise quiz
https://danlevy.net/javascript-promises-quiz/

what is wrong with below code
```js

const ar = [1,2,3,4]

// sequentially print no after 1 sec delay

function myPromise(num){
  return  new Promise(()=>{
    setTimeout(()=>{
        resolve(num)
    },1000);
  })
}

async function printSequentially(){
    for(let i = 0; i <ar.length ; i++) {
        const res = await myPromise(ar[i]);
        console.log(res);
    }
}
printSequentially()

```

### event loop
```javascript

/*

a > end >
  d > h > d > h > d > h > 
    newP > newP >newP
     b > 
       e > c > e >
          g> 
	    f>f>f

*/

console.log('stack [1] a');
setTimeout(() => console.log("macro [2] b"), 0);
setTimeout(() => console.log("macro [3] c"), 1);

const resolvedPromise = Promise.resolve();
for(let i = 0; i < 3; i++) {
    resolvedPromise.then(() => {
        console.log('stack [4] d');
	
	//micro
        new Promise((res,rej)=>{
            res('newP')
        })
        .then((response)=>{
            console.log(response)
        });
	
        setTimeout(() => {
            console.log('stack [5] e') //stack
            setTimeout(() => console.log("macro [5] f"), 0); //macro
            resolvedPromise.then(() => console.log('micro [6] g')); //micro
        }, 0);
	
       console.log("stack [7] h");
  });
}

console.log("macro [8] end")

/*
   stack : a , end 
   [           ] microtask
   [           ] macrotask

*/

```

```js

// output : b , c ,a

setTimeout(()=>{

 console.log('a')

},0)

Promise.resolve('success').then(()=>console.log('b'))

new Promise((res,rej)=>{
    res('c')
})
.then((response)=>{
    console.log(response)
})

```

### for event loop refer

https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/

https://developer.ibm.com/languages/node-js/tutorials/learn-nodejs-the-event-loop/



### Promises
https://danlevy.net/javascript-promises-quiz/
https://levelup.gitconnected.com/javascript-interview-questions-promises-400c51805cbe
https://medium.com/javascript-in-plain-english/6-interview-questions-that-combine-promise-and-settimeout-34c430fc297e
https://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html

### que: Promise all : what would happen if one of promise fail
### can you wrote polyfill for promise all



```javascript

var p = new Promise((resolve, reject) => setTimeout(() => { resolve(1); resolve(2) }, 1000))
p.then((val) => console.log("asynchronous logging has val:",val))

```

### que : output in below code

```javascript

console.log(10)

setTimeout(()=>{console.log(20)}, 1000)

setTimeout(()=>{console.log(30)}, 10)

console.log(40);

// could be fetch which resolve as per delay

new Promise((res,reject)=>{
  setTimeout(()=> res('done'),25)  // only 25 delay
})
  .then(res => console.log('res ',res))

function delay(milliseconds) {
  var start = new Date().getTime();
  for (var i = 0; i < 1e7; i++) {
    if ((new Date().getTime() - start) > milliseconds){
      break;
    }
  }
}


delay(3000);  // what is the output if we remove the delay

console.log(60);

```

### que : output in below code

```js

function test() {

    console.log(x);
    console.log(y);

  // setTimeout(()=> {
  //   console.log(x);
  //   console.log(y);
  // }, 1000);

  var x = 2;
  let y = 3;
}

test();
```

### que : microtask queue 
https://blog.risingstack.com/writing-a-javascript-framework-execution-timing-beyond-settimeout/


### que :

```javascript
https://javascript.info/async-await


const arrObj = [ { x: 3 }, { x: 9 }, { x: 5 }]



/* should print
wait 2 sec then print ist num then wait 2 sec then print next number in array
3
5
9
*/

const sortAndPrint = async (n, arrObj) => {

var t = n ;

arrObj.sort( (a,b)=>a.x - b.x  );

for(let i =0 ;i< arrObj.length ; i++){
    var promise = new Promise((resolve) => setTimeout(()=>resolve(arrObj[i],t)));
    var res = await promise ;
    console.log(res);
 }
  
}

sortAndPrint(2, arrObj)

```

### Que : Promise in a loop

```javascript
var promises = [];
 //let channels =[];

 [1, 2, 3, 4, 5].forEach((elm, i) => {

   promises.push(new Promise((resolve) => {
     setTimeout(() => { 
       //channels.push(elm); console.log(channels)
       resolve(elm);
     },  5000)  //setimeout is simulating operation like fetch
   }))

 });console.log("done")
 
 Promise.all(promises).then(() =>promises[0].then((x)=> console.log(x))) 
 
 ```

Without fetch like operation

```javascript

var promises = [];

 [1, 2, 3, 4, 5].forEach((elm, i) => {

   promises.push(new Promise((resolve) => {
       resolve(elm);
   }))

 });
 
 console.log("done")
 
 Promise.all(promises).then(() =>promises[0].then((x)=> console.log(x))) 
 ```

```Javascript


//get request Origin: http://localhost:3000

```js
    fetch("http://localhost:3000/api/person/:1") 
    .then((resp) => resp.json()) // Transform the data into json
    .then(function(data) {
     console.log(data)
         })
```
//gives cors error , unless you allow it on server
//Origin: http://localhost:3000

fetch("http://localhost:4000/api/person/:1") //http://localhost:4000/api/person/:1
	.then((resp) => resp.json()) // Transform the data into json
	.then(function(data) {
					
	   console.log(data)

	})
	
//to allow the cors on server
 
 app.get('/api/person/:id', function(req, res) {

    //allow cors
    res.header('Access-Control-Allow-Origin','*');
    res.header('Access-Control-Allow-Headers','X-Custom-Header,Origin,X-Requested-With,ContentType,Accept')
	// get that data from database
	res.json({ firstname: 'John', lastname: 'Doe' });
});
				
```
```javascript 

// output in what order, after how many sec
 alert('hello')

 setTimeout(()=>{
 console.log('1000')
 },1000)

  setTimeout(()=>{
     console.log('5000')
 },5000)
 
 ```
 // Promisify functions that accept the last argument as the callback fn.

```js
	
	function sumThree (a,b,c, callback) {
setTimeout(()=>{
 callback(null, a+b+c)
},1000)
}

function promisify(func) {
//   add code here
  
 return (...ar){
 return new Promise((res,rej){
      
 let result = func(...ar);
  if(result)
   })
  }
 }

 const sumThreePromisifed = promisify(sumThree);

 sumThreePromisifed(1, 2, 3)
  .then((sum) => console.log(' sum is ', sum))
   .catch((err) => console.log(' err is', err));

```js
// promise any 
// returns a resolved promise ..only if a promise is resolved

const promise1 = Promise.reject(`reject promise`);
const promise2 = new Promise((resolve) => setTimeout(resolve, 100, 'quick promise'));
const promise3 = new Promise((resolve) => setTimeout(reject, 500, 'slow promise'));

const promises = [promise1, promise2, promise3];

Promise.any(promises).then((value) => console.log(value));
```	

#### https://v8.dev/blog/fast-async

#### https://exploringjs.com/es6/ch_promises.html

#### https://betterprogramming.pub/javascript-promise-know-when-to-use-it-and-how-it-works-b8671e585e53

#### https://www.coreycleary.me/how-to-rewrite-a-callback-function-in-promise-form-and-async-await-form-in-javascript/


#### https://tusharsharma.dev/posts/retry-design-pattern-with-js-promises

#### https://alligator.io/js/promise-all-promise-race/

#### https://www.twilio.com/blog/asynchronous-javascript-choosing-the-right-asynchronous-tool

#### https://www.twilio.com/blog/asynchronous-javascript-understanding-callbacks

#### https://skilled.dev/course/build-a-javascript-promise

#### https://james-priest.github.io/udacity-nanodegree-mws/course-notes/javascript-promises.html

