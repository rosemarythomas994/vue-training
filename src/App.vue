<script setup lang="ts">
import { ref, computed, watch  } from 'vue'


const count = ref(0)
const url = ref('https://picsum.photos/200/300') // or any image path
const url1 = 'https://vuejs.org/guide/introduction';
const imageUrl = 'https://vuejs.org/images/logo.png';
const isActive = true;
const color = 'blue';
const checked = ref(false);
const selected = ref('');
const isLoggedIn = ref(true);
const role = ref('admin');
const show = ref(true);
const items = ['Apple', 'Banana', 'Orange'];
const person = { name: 'John', age: 30, city: 'Paris' };
const hover = ref(true);
const message = 'Hello from v-text!';
const rawHtml = '<strong>This is bold</strong>';
const score = ref(0);
const username = ref('');
const username1= ref('');
const studentname = ref('')
const helloMessage = ref('')

const double = computed(() => count.value * 2)

watch(count, (newValue, oldValue) => {
  console.log(`Count changed from ${oldValue} to ${newValue}`)
})

function greet() {
  alert(`Hello, ${username1.value || 'Guest'}!`);
}

function onInput(event: Event) {
  const target = event.target as HTMLInputElement
  console.log(target.value)
} //This function is triggered when the user types something into an <input> field.
// event is the default event object passed by the browser.
// event.target is the element that triggered the event (e.g., the <input> element).
// TypeScript doesn't know what kind of element target is, so we cast it using as HTMLInputElement to access .value.
// Finally, it logs the input's current value to the console.
function sayHello(name: String) {
  alert(`Hello, ${name}!`)
}//This function takes a name as a string parameter.
// It shows an alert box that says "Hello, [name]!"

function studentHello(name: string) {
  if (name.trim()) {
    alert(`Hello, ${name}!`)
  } else {
    alert('Please enter a name!')
  }
}


</script>

<template>
<div>
  <div>
                <h1>Who pays the bill</h1>
            </div>
  <div id="app">
    <button @click="count++">
      Count is: {{ count }}
    </button>
  </div>
  <div id="app">

    <img :src="url" alt="Bound image" width="300" />
  </div>
  <div>
    <h2>Welcome to Vue.js</h2>
  </div>

  <div class="hello-box">
    Hello World
  </div>
  <div>
    <a :href="url1">Go to Site</a>
  </div>
  <div><img v-bind="{ src: imageUrl, alt: 'Vue Logo' }" />
  </div>
  <div :class="{ active: isActive }" :style="{ color: color }">
    Dynamic class and style
  </div>

<div>
  <input v-model="username" />
  <p>Hi, {{ username }}</p>

</div>


<div>
      <input v-model="username1" placeholder="Enter username" />

    <button @click="greet">Click Me</button>
</div>
<div>
  <input type="checkbox" v-model="checked" />
<p>Checked: 
  {{ checked }}</p>
</div>
<select v-model="selected">
  <option disabled value="">Please select</option>
  <option>Vue</option>
  <option>React</option>
</select>

<div>
<p v-if="isLoggedIn">Welcome!</p>
<p v-else>Please log in</p>
</div>

<div>
<p v-if="role === 'admin'">Admin Panel</p>
<p v-else-if="role === 'user'">User Dashboard</p>
<p v-else>Guest</p>
</div>
  <div>
    <label>Enter Score: </label>
    <input type="number" v-model="score" />

    <p v-if="score >= 90">🎉 Excellent (A Grade)</p>
    <p v-else-if="score >= 60">🙂 Good (B Grade)</p>
    <p v-else>😢 Needs Improvement (F Grade)</p>
  </div>
<div>
<button @click="show = !show">Toggle</button>
<p v-show="show">Now you see me</p>
</div>


<div>
<ul>
  <li v-for="(item, index) in items" :key="index">
    {{ index + 1 }}. {{ item }}
  </li>
</ul>
</div>

<div><ul>
  <li v-for="(value, key) in person" :key="key">
    {{ key }}: {{ value }}
  </li>
</ul></div>


<div><button @click="count++">Count: {{ count }}</button></div>


<div @mouseover="hover = true" @mouseleave="hover = false">
  Hover: {{ hover }}
</div>

<div><p v-text="message"></p></div>
<div v-html="rawHtml"></div>

<div><p v-once>This will never update: {{ count }}</p></div>

<div><input @input="onInput($event)" />
<button @click="sayHello('Vue')">Say Hello</button>

</div>

<div>
<input v-model="studentname" placeholder="Enter your name" />
  <button @click="studentHello(studentname)">Say Hello</button>
</div>

<div>
  <h2>Cmputed properties</h2>
   <p>Count: {{ count }}</p>
     <p>Double: {{ double }}</p>
   <button @click="count++">Increment</button>
</div>


<div>

 <h1>Watch Example</h1>
<p>Count: {{ count }}</p>

 <button @click="count++">Increment</button>
</div>




</div>

</template>



<style scoped>
.hello-box {
  background-color: #90ee90;
  /* light green */
  color: #000;
  padding: 12px 20px;
  font-size: 20px;
  border-radius: 8px;
  margin-top: 20px;
  width: fit-content;
}
</style>


