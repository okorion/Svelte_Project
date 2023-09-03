<script>
	import { writable } from 'svelte/store';
	import Post from './Post/Post.svelte';

	let id = 0;
	let title = '';
	let date = new Date();
	let posts = writable([]);
</script>

<a href="/board/write">게시글 작성하기</a>

<table>
	<tr>
		<th>번호</th>
		<th>제목</th>
		<th>작성자</th>
		<th>작성일</th>
	</tr>
	{#each $posts as post}
		<Post {post} />
	{/each}
</table>

<style>
	a {
		display: block;
		text-align: center;
		background-color: white;
		color: black;
		border: 3px solid #555555;
		width: 20vh;
	}
</style>
