<template>
	<div class="todo-add">
		<input class="todo-add__input"
			   v-model="newItem"
			   @keyup.enter="[$emit('insertTodo', newItem), 
			   				  clean()]"
			   placeholder="Например, купить печенье">
		<button class="todo-add__button"
				@click="[$emit('insertTodo', newItem)], 
						 clean() ">
			Добавить
		</button>	
	</div>
</template>

<script>
export default {

  name: 'AddTodo',

  data () {
    return {
    	newItem: ''
    }
  },

  methods: {  
  	clean() {
  		this.newItem = '';
  	}
  },

};
</script>

<style lang="css" scoped>

.todo-add {
	width:  60%;
	display: flex;
	justify-content: space-between;
}

.todo-add__input {
	width: 80%;
	height: 36px;
	padding: 12px;
	border: 1px solid orange;
	border-radius: 5px;
}

.todo-add__button {
	background-color: white; 
	color: black; 
  	border: 2px solid #008CBA;
	border-radius: 5px;
	height: 36px;
	cursor: pointer;
	padding: 0px 16px;
	font-size: 16px;
	transition-duration: 0.4s;
	cursor: pointer;
}

.todo-add__button:hover {
	background-color: #008CBA;
  	color: white;
}

</style>
