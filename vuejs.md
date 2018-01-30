# vue.js ????,????,filter
---
html????
```
v-bind:class = :class 
```

html????????

```
{{ title }}
```

---
```
v-on:input
```
????

---
filter

---
```
title | uppercase
```

---

test.html
```
<html>
<head>
	<meta charset="UTF-8">
	<title>vue.js??</title>
	<script src="https://unpkg.com/vue/dist/vue.js"></script>
	<link rel="stylesheet" href="style.css">
</head>
<body>
	<div id="app">
		<p>vuejs??:https://jsfiddle.net vue.js????</p>

		<button v-on:click="title='??'">???:????</button>
		<button v-on:click="changeTitle">???:????</button>
		<p>{{ title }}</p>
		<p>{{ title | uppercase }}</p>
		<p>{{ title | uppercase | lowercase}}</p>
		<p>{{ theTitle }}</p>
		
		<input type="text" v-on:input="cssClass=$event.target.value">
		<p v-bind:class="cssClass">Class:{{ cssClass }}</p>
		<p :class="cssClass">Class:{{ cssClass }}</p>
	</div>
</body>
</html>
<script>
	Vue.filter('uppercase',function(value){
		return value.toUpperCase();
	});
	new Vue({
		el:'#app', // element
		data:{ // ??????
			cssClass:'' ,
			title:'hello world',
			message: 'something'
		},
		methods:{
			changeTitle(){
				this.title = '????';
			}
		},
		computed:{
			theTitle:function(){
				return this.title.toUpperCase();
			}
		},filters:{
			lowercase: function(value){
				return value.toLowerCase();
			}
		}

	});
</script>
```
 
---

style.css

```
.red
{
	background-color: red;
}

.blue
{
	background-color: blue;
}

.user
{
	borader: 1px solid #ccc;
	background-color: white;
	padding: 10px;

}
```

---

vuejs ????

---

```
<html>
<head>
    <meta charset="UTF-8">
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <title>vuejs ????</title>
</head>

<body>
    <div id="app">
        <button v-on:click="increment">??</button>
        <p>???: {{ counter }}</p>
        <p>???: {{ clicks }}</p>
    </div>
</body>

</html>
<script>
	new Vue({
		el:'#app',
		data:{
			//counter:0, // vuejs ??????????
			clicks:0
		},
		methods:{
			increment(){
				this.clicks++;
				// this.counter=this.clicks*2;
			}
		},
		computed:{  //vuejs ????
			counter(){
				return this.clicks*2;
			}
		}
	});
</script>
```
---
????
```
<html>
<head>
	<meta charset="UTF-8">
	<title>VUEJS?????</title>
	<script src="https://unpkg.com/vue/dist/vue.js"></script>
</head>
<body>
	<div id="app">
		<button v-on:click="isShow">??/???</button>
		<p v-if="show">???????</p>
		<p v-else>???????</p> <!-- ?????? -->
		<p v-show="show">haha</p> <!-- css display: none; ??-->
		<hr>
		<ul>
			<li v-for="(person,id) in persons">{{ person.name }} {{ id }}</li>
		</ul>
	</div>
</body>
</html>

<script>
	new Vue({
		el:"#app",
		data:{
			show:true,
			persons:[
				{name:'lpz',age:42},
				{name:'lph',age:30},
				{name:'lym',age:12}
			]
		},
		methods:{
			isShow(){
				this.show = !this.show;
			}
		}
	});
</script>
```
---

vue.js ????

```
<html>

<head>
    <meta charset="UTF-8">
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <link rel="stylesheet" href="style.css">
    <title>vue ????</title>
</head>

<body>
    <div id="app">
        <p>{{ title }}</p>
        <hr>
        <div>
            <!-- <p>???: {{  username }}</p> -->
            <!-- <div class="user" v-for="user in users"><p>???: {{ user.username }}</p></div> -->
            <app-user></app-user>  <!-- 3.???????? -->
            <app-user></app-user>
        </div>
    </div>
</body>

</html>
<script>
// ?????component
/*Vue.component('app-user',{
		data: function(){
			return {
				users: [
					{username: 'lpz'},
					{username:'lph'},
					{username:'lym1'}
				]
			};
		},*/ 

/*template:'<div><div class="user" v-for="user in users"><p>???: {{ user.username }}</p></div></div>'*/
/*template:`<div>
		<div class="user" v-for="user in users">
		<p>???1: {{ user.username }}</p>
		</div>
		</div>`
	});*/
new Vue({
    el: "#app",
    data: {
        title: 'hello world!',
        // username:'lpz'
        /*users: [
        		{username: 'lpz'},
        		{username:'lph'},
        		{username:'lym'}
        ]*/
    },
    components: {  // ????????????
        'app-user': { // ????Vue???
            	data: function() {
                    return {
                        users: [
                            { username: 'lpz' },
                            { username: 'lph' },
                            { username: 'lym1' }
                        ]
                    };
            	},
            	template: `<div>
					<div class="user" v-for="user in users">
					<p>???1: {{ user.username }}</p>
					</div>
					</div>`
        }
    }
});
</script>
```

---
vue cli??
```
<!--
	
	 npm install -g vue-cli
	 https://github-vuejs-templates/webpack
	 vue init webpack-simple vue-webpack
	 cd vue-webpack
	 npm install 
	 npm run dev
	 -->
 ```

---
vue-cli ????



main.js

```
import Vue from 'vue'
import App from './App.vue'
import VueRouter from 'vue-router'
import Message from './Message.vue'
import Users from './Users.vue'
import Home from './Home.vue'
Vue.use(VueRouter);

const routes = [
	/*{ path: '/users', component: Users },*/
	{ path: '/users/:teamId', component: Users },
	{ path: '/', component: Home }
];

const router = new VueRouter({
	routes:routes,
	mode:'history'
});

Vue.component('app-message',Message);
new Vue({
  el: '#app',
  router:router,
  render: h => h(App)
});

```

App.vue

```
<template>
  <div id="app">
    <app-message></app-message>
    <h1>????</h1>
    <hr>
    <!-- <a href="/">Home</a> -->
    <router-link to="/">Home</router-link>
    <router-link to="/users">Users</router-link>
    <router-link to="/users/10">Users 10</router-link>
    <router-link to="/users/12">Users 10</router-link>
    <hr>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      
    }
  }
}
</script>

<style lang="scss">
</style>

```

Message.vue

```
<template>
	<div>
		<!-- <h1>???!</h1> -->
		<h1>Message???message: {{ message }}</h1> 
		<app-input :msg="message" @messageChanged="message = $event"></app-input>
		<!-- 
		
		3.1 @messageChanged="message=$event" ??$emit ?????messageChanged
		3.2 :msg="message" ?app-input??,???Input
		-->
	</div>
</template>
<script>
	import Input from './Input.vue'; //??Input.vue????
	export default{
		data(){
			return {
				message: '???'
			} 
		},
		components:{
			'app-input':Input // ??Input???app-input??
		}
	}
</script>
```

Input.vue
```
<template>
	<div>
		<p>?????????:{{ msg }}</p>
		<!-- <input type="text" v-model="message"></input> -->
		<!-- <input type="text" :value="msg"></input> -->
		<input type="text" :value="msg" @input="changeMessage"></input>
		<p>{{message}}</p> <!-- 1.input???????changeMessage?? -->
	</div>
</template>
<script>
//?JavaScript ES6?,export?export default??????????????????,??????????????import+(?? | ?? | ?? | ??)????,????,??????????,??????????,export?import?????,export default????? 
	export default{
		props:['msg'], //“prop” ??????????,??????????????????? props ?? ?? props
		data(){
			return {
				message:''
			}
		},
		methods:{
		// 2.1 event.target.value??input?????,???????message??,message????,?????message?????	
		// 2.2??messageChanged??
			changeMessage(){
				this.message = event.target.value;		this.$emit('messageChanged',this.message);
			}
		}
	}
</script>

```

vue.js router
```
npm install vue-router
```
Home.vue
```
<template>
	<h1>??</h1>
</template>
```
Users.vue
```
<template>
	<div>
	<h1>????</h1>
	<p>??id?: {{ $route.params.teamId }}</p>
	<button @click="goHome">???</button>
	</div>
</template>

<script>
	export default{
		watch:{
			'$route'(to,from){
				alert(to.params.teamId);
			}
		},
		created(){
        	alert(this.$route.params.teamId);
      	},
      	methods:{
      		goHome(){
      			this.$router.push('/');
      		}
      	}
	}

</script>
```





