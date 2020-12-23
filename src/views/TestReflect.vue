<template>
  <div>Reflect</div>
</template>
<script>
export default {
  name: 'Reflect',
  setup(props, context) {
    setTimeout(() => {
      console.log('sync: 3')
    }, 0);
    let p2 = Promise.resolve('promise: 2')
    p2.then(function(s) {
      console.log(s)
    })
    console.log('log 1')

    const p3 = Promise.reject('error')
    p3.then(null, function(s) {
      console.log(s)
    })
    const preLoadImage = function(path) {
      return new Promise(function (resolve, reject) {
        const image = new Image()
        image.onload = resolve
        image.onerror = reject
        image.src = path
      })
    }
    preLoadImage('https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3104938644,4157394168&fm=26&gp=0.jpg')
    
    let p4 = new Promise((resolve, reject) => {
      resolve('hello')
    })
    let p5 = new Promise((resolve, reject) => {
      throw new Error('p5报错了')
    }).then(res => res)
      .catch(e => e)
    Promise.all([p4,p5])
    const resolved = Promise.resolve(42)
    const rejected = Promise.reject(-1)
    const allSettledPromise = Promise.allSettled([resolved, rejected])
    allSettledPromise.then(function(res) {
      console.log(res)
    })

    .then(res => console.log(res))
    .catch(e => console.log(e))

    return {

    }
  }
}
</script>