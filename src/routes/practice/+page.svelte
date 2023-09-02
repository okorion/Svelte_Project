<script>
	import {writable} from 'svelte/store';
	import ToDo from './ToDo/ToDo.svelte';

	let name = 'world';
	let title = '';
	let todos = writable([]);
	let id = 0;

	function createToDo() {
		$todos.push({ id, title });
		$todos = $todos; // 할당을 통해 반응성 추가
		title = '';
		id++;
	}
</script>

<h1>Hello {name}!</h1>

<div class="board">
	<input
		bind:value={title}
		type="text"
		on:keydown={(e) => {
			e.key === 'Enter' && createToDo();
		}}
	/>
	<button on:click={createToDo}> 작성하기 </button>
</div>

{#each $todos as todo}
	<div>
		<ToDo {todos} {todo} />
	</div>
{/each}

<style>
	.board {
		display: flex;
		flex-direction: row;
	}
</style>
