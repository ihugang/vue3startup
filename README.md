# vue3startup
vue3 learn 

## 主要学习方向：SFC (Single-File Components) 和 组合式API (Composition API)
```javascript    
<script setup>
import { ref, onMounted } from 'vue'
// 响应式状态
const count = ref(0)

// 用来修改状态、触发更新的函数
function increment() {
  count.value++
}

// 生命周期钩子
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>

<style>
.greeting {
  color: red;
  font-weight: bold;
}
</style>
```
个人比较喜欢 **组合式 API + 单文件组件**

一个编译后的 SFC 是一个标准的 JavaScript(ES) 模块，在构建配置正确的前提下，你可以像导入其他 ES 模块一样导入 SFC.

1. 插值 将js对象值绑定到网页元素中

 - Mustache语法（文本绑定）
```javascript
<span>Message: {{ msg }}</span>
```
 - 原始HTML
```vue
<p>Using text interpolation: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```
2. 属性绑定 : 与动作绑定 @ ,修饰符 .prevent
```html
<a :[attributeName]="url"> ... </a>
<a @[eventName]="doSomething">
<form @submit.prevent="onSubmit">...</form>

```
3. 变量和对象的响应式封装 ref & reactive **Vue 的响应式系统的最佳实践是 仅使用你声明对象的代理版本。**
```js
const a = ref(0)
const b = ref(false)
const c = ref("hello world")

const d = reactive({
  name: 'Jane',
  age: 23,
  friends:[{
    name: 'Tome',
    age:20
    }]
})

let count = $ref(0)   // Notice

function increment() {
  // 无需 .value
  count++
}

const raw = {}
const proxy = reactive(raw)

// 代理对象和原始对象不是全等的
console.log(proxy === raw) // false

// 在js中对ref对象赋值，需要用.value，例如：
a.value = 1

<template>
  <button @click="increment">
    {{ a }} <!-- 无需 .value -->
  </button>
</template>
```



