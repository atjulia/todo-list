<template>
	<div id="app">
		<h1>Todo List</h1>
		<NewTask @taskAdded="addTask"/>
		<TaskGrid :tasks="tasks" />
	</div>
</template>

<script>
import NewTask from "./components/NewTask.vue";
import TaskGrid from './components/TaskGrid.vue'

export default {
	components: { TaskGrid, NewTask },
	data () {
		return {
			tasks: [
				{ name: 'Lavar', pending: false },
				{ name: 'Comprar', pending: true }
			]
		}
	},
	methods: {
		addTask (task) {
			const sameName = t => t.name === task.name
			const reallyNew = this.tasks.filter(sameName).length === 0
			if(reallyNew) {
				this.tasks.push({
					name: task.name,
					pending: task.pending || true
				})
			}
		}
	}
}
</script>

<style>
	body {
		font-family: 'Inter', sans-serif;
		background: #17181E;
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
