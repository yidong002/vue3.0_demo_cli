<template>
  <div>Reflect</div>
</template>
<script>
export default {
  name: 'Reflect',
  setup(props, context) {
    let arr = [{a:1,b:2},{pong:'pang',code:'code'},{a:1,b:2}]
    // let arr = [{a:1,b:2},{code:'code'},{a:1,b:2}]
    // let arr = [{a:1,b:2},{pong:'pang'},{a:1,b:2}]
    // arr.map(v => {
    //   if(v.hasOwnProperty('pong') && v.hasOwnProperty('code')) {
    //     console.log('全部')
    //   } else if(v.hasOwnProperty('pong') && !v.hasOwnProperty('code')) {
    //     console.log('pong')
    //   } else if(v.hasOwnProperty('code') && !v.hasOwnProperty('pong')) {
    //     console.log('code')
    //   }
      
    // })
    // for(let item of arr) {
      // if(item.hasOwnProperty('code') && item.hasOwnProperty('pong')) {
      //   console.log('全部')
      //   break
      // } else if(item.hasOwnProperty('code') && !item.hasOwnProperty('pong')) {
      //   console.log('code')
      //   break
      // } else if(!item.hasOwnProperty('code') && item.hasOwnProperty('pong')) {
      //   console.log('pong')
      // } else {
      //   console.log('nothing')
      // }
    // }
    
    // let p1 = new Promise((resolve, reject) => {
    //   resolve('hello1')
    // })
    // let p2 = new Promise((resolve, reject) => {
    //   throw new Error('报错了') 
    // })
    // let p3 = new Promise((resolve, reject) => {
    //   resolve('hello3')
    // })
    // const p = Promise.any([p1,p2,p3])
    // console.log(p)
    var it = makeIterator(['a','b'])
    console.log(it.next())
    console.log(it.next())
    console.log(it.next())

    //**********模拟iterator遍历器********* */
    function makeIterator(array) {
      let nextIndex = 0;
      return {
        next: function() {
          return nextIndex < array.length ? {value: array[nextIndex++]} : {done: true}
        }
      }
    }
    let myIterable = {
      [Symbol.iterator]: function* (){
        yield 1;
        yield 2;
        yield 3;
      }
    }
    console.log([...myIterable])
    
    function* helloWorldGenerator() {
      yield 'hello';
      yield 'world';
      yield [...myIterable]
      yield console.log(this)
      return 'ending'

    }
    var hw = helloWorldGenerator()
    for (let v of hw) {
        console.log(v)
    }
    return {

    }
  }
}
</script>