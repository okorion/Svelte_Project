<script>
	export let todo;
	export let todos;

	let isEdit = false;
	let title = '';

	function onEdit() {
		isEdit = true;
		title = todo.title;
	}
	function offEdit() {
		isEdit = false;
	}
	function updateToDo() {
		todo.title = title;
		offEdit();
	}
	function deleteToDo() {
		$todos = $todos.filter((t) => t.id !== todo.id);
		console.log(todos);
	}
</script>

{#if isEdit}
	<div>
		<input
			bind:value={title}
			type="text"
			on:keydown={(e) => {
				e.key === 'Enter' && updateToDo();
			}}
		/>
		<button on:click={updateToDo}> 수정완료 </button>
		<button on:click={offEdit}> 취소 </button>
	</div>
{:else}
	<div>
		{todo.title}
		<button on:click={onEdit}> 수정하기 </button>
		<button on:click={deleteToDo}> 삭제 </button>
	</div>{/if}
