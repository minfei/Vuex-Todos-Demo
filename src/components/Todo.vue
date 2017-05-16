<template>
	<div id="app">
		<header>
			<h1>Hello Todos！</h1>
			<input placeholder="请输入内容..." v-model="todoTitle" @keyup.enter="addTodo(todoTitle)">
		</header>
		<section v-show="todos.length">
			<li v-for="todo in todos">
				{{ todo.todoTitle }}
				<button @click="delTodo(todo)">删除</button>
			</li>
		</section>
	</div>
</template>
<script>
	export default {
		name:'todo',
		data() {
			return {
				todoTitle: '',
				error:''
			}
		},
		computed: {
			todos() {
				return this.$store.state.todos
			}
		} ,
		methods:{
			addTodo: function(todoTitle){
				if(todoTitle != ''){
						this.$store.commit('addTodo',{todoTitle:todoTitle});
						this.todoTitle='';
				}
			},
			delTodo: function(todo) {
				this.$store.commit('delTodo',{todo:todo})
			}
		}
	}

</script>
