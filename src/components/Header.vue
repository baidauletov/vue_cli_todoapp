<template>
	<div class="header">
		<h1>Todo List</h1>
	</div>
</template>

<script>
export default {
	name: 'Header',
};
</script>

<style scoped>

h1 {
	font-size: 56px;
}

.header {
	display: flex;
	justify-content: center;
	align-items: center;
	background: rgb(89,86,138);
	background: linear-gradient(90deg, rgba(89,86,138,1) 0%, rgba(0,212,255,1) 100%);
	height: 100px;
}

</style>
