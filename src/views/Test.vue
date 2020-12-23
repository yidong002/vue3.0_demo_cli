<template>
  <div>Test</div>
</template>

<script>
export default {
  name: 'Test',
  setup() {
    var obj = new Proxy({},{
      get: function(target, key, recevier) {
        console.log(`getting ${key}`)
        return Reflect.get(target, key, recevier)
      },
      set: function(target, key, value, recevier) {
        if (value) {
          console.log(`setting ${key}-${value}-${target.count}`)
          return Reflect.set(target, key, value, recevier)

        } else {
          console.error('Plase push a valid with obj')
          value = 3
          return Reflect.set(target, key, value, recevier)
        }
      },
      has: function(target, propKey) {
        console.log(`has ${propKey}`)
        return Reflect.has(target, propKey)
      },
      deleteProperty: function(target, propKey) {
        console.log(`deleteProperty ${propKey}`)
        return Reflect.defineProperty(target, propKey)
      },
      ownKeys: function(target) {
        console.log(`ownKeys ${target}`)
        return Reflect.ownKeys(target)
      },
      getOwnPropertyDescriptor: function(target, propKey) {
        console.log(`getOwnPropertyDescriptor ${propKey}`)
      },


    })
    let target = {}
    let handler = {}

    let { proxy, revoke } = Proxy.revocable(target, handler)
    proxy.foo = 123
    revoke()
    proxy.foo
    obj.count = 0
    ++obj.count
    console.log(obj.count)
    return {

    }
  }
}
</script>