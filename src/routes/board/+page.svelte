<script>
	import { posts } from './posts.js';
	import Post from './Post/Post.svelte';
</script>

<a href="/board/write">게시글 작성하기</a>
<!-- <button style="height: 20px;" on:click={() => console.log($posts, posts)} /> -->

<table>
	<tr>
		<th>번호</th>
		<th>제목</th>
		<th>내용</th>
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
