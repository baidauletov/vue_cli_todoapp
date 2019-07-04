<template>
	<div class="todo">
		<h1 class="todo__header">Todo</h1>
		<AddTodo class="todo__add"
				 @insertTodo="addItem" />
		<ul class="todo-list">
			<TodoItem class="todo-list__item"
					  v-for="todo in todos" 
					  :todo="todo" 
					  :key="todo.id"
					  @deleteTodo="delItem"
					  @doneItem="editItem"
			/>
		</ul>
	</div>
</template>

<script>
import AddTodo from './AddTodo.vue'
import TodoItem from './TodoItem.vue'

export default {

  name: 'TodoList',

  components: {
  	AddTodo,
  	TodoItem,
  },

  data () {
    return {
    	todos: [
    		{
    			id: '12345',
    			text: 'купить 10 бургеров',
    			completed: true
    		},
    		{
    			id: '2345',
    			text: 'съесть 10 бургеров',
    			completed: false
    		},
    		{
    			id: '56324',
    			text: 'выпить воды',
    			completed: false
    		}
    	]
    }
  },

  methods: {
  	addItem(text) {
  		text ? this.todos.unshift({ id: new Date().getTime().toString(),
  									text: text,
  									completed: false
  								})  
  			 : null;
  	},
  	delItem(id) {
  		let pos = this.todos.map(x => x.id).indexOf(id);
  		this.todos.splice(pos, 1);
  	},
  	editItem(item) {
  		this.todos[item.id].text = item.text;
  	}
  },
};
</script>

<style lang="css" scoped>


.todo {
	display: flex;
	flex-direction: column;
	width: 80%;
	align-items: center;
	margin: 0 auto;
	margin-bottom: 40px;
	min-height: 450px;
}

.todo__header{
	align-self: flex-start;
	margin: 30px;
	font-size: 56px;
}

.todo__add {
	margin-bottom: 20px;
	font-size: 20px;
}
	
.todo-list {
	display: flex;
	flex-direction: column;
	align-items: center;
	width: 100%;
}

.todo-list__item {
	margin-top: 8px;
	padding-left: 12px;
}

</style>
