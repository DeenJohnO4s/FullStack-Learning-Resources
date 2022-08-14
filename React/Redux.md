### Mastering Redux 
    
- **Getting Started with Redux**   
https://egghead.io/courses/getting-started-with-redux

https://medium.com/@justin3737/getting-started-with-redux-dded45556673

https://github.com/tayiorbeii/egghead.io_redux_course_notes

https://learnreduxwithdanabramov.com/
  
 - **good tutorial**
  https://github.com/happypoulp/redux-tutorial
  
- **Simple Redux**
 https://bumbu.me/simple-redux/
 
- **why bind action creators**
 https://stackoverflow.com/questions/41754489/when-would-bindactioncreators-be-used-in-react-redux
 
 Cory house has given a great explaination of why use bind action creator and when in his course 
 Building Applications with React and Redux in ES6 - pluralsight 
  
- **Building React Applications with Idiomatic Redux**
https://github.com/tayiorbeii/egghead.io_idiomatic_redux_course_notes
    
 - **React-redux "connect" explained**
 
  https://www.sohamkamani.com/blog/2017/03/31/react-redux-connect-explained/
  https://blog.logrocket.com/react-redux-connect-when-and-how-to-use-it-f2a1edab2013/
  
 https://github.com/gaearon/redux-thunk
 https://stackoverflow.com/questions/35411423/how-to-dispatch-a-redux-action-with-a-timeout/35415559#35415559
 
 https://medium.com/netscape/advanced-redux-action-types-d5a71ed44e16
 
 https://github.com/reactjs/redux/issues/1824#issuecomment-228585904
 http://krasimirtsonev.com/blog/article/my-take-on-redux-architecture
 
 ### Thunk & middlewares
 
 https://medium.com/fullstack-academy/thunks-in-redux-the-basics-85e538a3fe60
 
 
 https://stackoverflow.com/questions/34570758/why-do-we-need-middleware-for-async-flow-in-redux?noredirect=1&lq=1
 https://stackoverflow.com/questions/35411423/how-to-dispatch-a-redux-action-with-a-timeout/35415559#35415559
 
 
 https://daveceddia.com/what-is-a-thunk/ 
 https://alligator.io/redux/redux-thunk/
 https://github.com/tylerlong/hello-async
 
 https://github.com/reactjs/redux/blob/master/src/applyMiddleware.js
 https://github.com/gaearon/redux-thunk/blob/master/src/index.js
 
 https://github.com/reactjs/redux/issues/1088
 
 https://medium.com/@stowball/a-dummys-guide-to-redux-and-thunk-in-react-d8904a7005d3?source=search_post
 http://blog.isquaredsoftware.com/2016/10/idiomatic-redux-why-use-action-creators/
 
 #### how to build your own redux (very good)
 https://zapier.com/engineering/how-to-build-redux/
 
  ### Redux saga 
  https://medium.com/agency04/the-redux-saga-continues-implementing-your-own-redux-saga-like-middleware-f93a23ed840
  
  https://medium.com/appsflyer/dont-call-me-i-ll-call-you-side-effects-management-with-redux-saga-part-2-cd16f6bcdbcd
  
  https://medium.com/nmc-techblog/the-power-of-redux-saga-3dbd26a08b49 (great)
  
  https://javascript.plainenglish.io/redux-thunk-vs-redux-saga-8c93fc822de
  
  https://stackoverflow.com/questions/54627603/using-redux-saga-in-a-big-project
  
  
  ```js
  // https://www.youtube.com/watch?v=o3A9EvMspig

function request() {
   var p = fetch("https://rickandmortyapi.com/api/character//?name=Rick");
   p.then((res) => res.json())
   .then((x)=>{
     it.next(x)
   });

}

function* main(){
  var res = yield request();
  console.log(res);
}

var it = main(); //start
it.next();

  ```
 https://www.youtube.com/watch?v=o3A9EvMspig
 
 https://www.youtube.com/watch?v=ByQknrU42mY
 
https://flaviocopes.com/redux-saga/

https://medium.com/agency04/the-redux-saga-continues-implementing-your-own-redux-saga-like-middleware-f93a23ed840

https://medium.com/takeaway-tech/getting-started-with-redux-saga-54af359e84ff

https://levelup.gitconnected.com/react-native-redux-implementing-redux-saga-for-an-asynchronous-flow-90a0e9d7d8e8
 
 
 
 ***redux saga**

 https://vhudyma-blog.eu/2020-07-25-redux-thunk-vs-redux-saga-the-differences/

https://medium.com/@shoshanarosenfield/redux-thunk-vs-redux-saga-93fe82878b2d

https://stackoverflow.com/questions/50285972/what-is-the-difference-between-redux-thunk-and-redux-saga

https://www.eternussolutions.com/2020/12/21/redux-thunk-redux-saga/

https://blog.devgenius.io/react-redux-middlewares-thunk-vs-saga-e346a25319b3

