<template>
	<div class="todo-item">
		<div class="wrapper"
			 v-show="editItemId != todo.id">
			<span class="todo-item__text"
				  :class="{'todo-item_done' : todo.completed}"
			  	  @click="itemComplete"
			  	  @dblclick="editItem(todo.id)">
		 		{{ todo.text }}
			</span>
			<button class="todo-item__delete"
				@click="$emit('deleteTodo', todo.id)">
				<i class="fa fa-trash-o" aria-hidden="true"></i>
			</button>

		</div>
		<input class="todo-item__edit"
			   v-show="editItemId == todo.id"
			   v-model.trim='todo.text'
			   @keyup.enter="[$emit('doneItem', todo), closeEdit()]"
			   @keyup.esc="closeEdit()">
	</div>
</template>

<script>
export default {

  name: 'TodoItem',
  props: ['todo'],

  data() {
  	return {
  		editItemId: '',
  	}
  },

  methods: {
  	itemComplete() {
  		this.todo.completed = !this.todo.completed;
  	},
  	editItem(id) {
  		this.editItemId = id; 
  	},
  	closeEdit() {
  		this.editItemId = null;
  	}
  },

};
</script>

<style lang="css" scoped>

.todo-item {
	display: flex;
	justify-content: space-between;
	width: 60%;
	padding-bottom: 4px;
	border-bottom: 1px solid gray;
}

.wrapper {
	display: flex;
	justify-content: space-between;
	width: 100%;
}

.todo-item__text {
	width: 90%;
	font-size: 20px;
	cursor: pointer;
}

.todo-item_done {
	text-decoration: line-through;
}

.todo-item__delete {
	height: 30px;
	min-width: 30px;
	border: none;
	border-radius: 5px;
	cursor: pointer;
}

.todo-item__delete:hover {
	background-color: #fff;
	border: 2px solid rgb(18,135,158);
}

.todo-item__edit {
	width: 100%;
	height: 36px;
	padding: 12px;
	font-size: 20px;
	border: 1px solid gray;
	border-radius: 5px;	
}

</style>
