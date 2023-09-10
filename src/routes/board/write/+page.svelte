<script>
	import { posts } from '../posts.js';

	let title;
	let content;
	let id = 1;
	let time = new Date();

	function updateTime() {
		time = new Date();
	}

	// 매 초마다 시간 업데이트
	setInterval(updateTime, 1000);

	function write() {
		if (!title.trim()) {
			title = '';
			return;
		}

		posts.update(($posts) => [
			{
				id,
				title,
				content,
				time: new Date().toLocaleDateString()
			},
			...$posts
		]);

		title = '';
		content = '';
		id++;
		alert('작성완료');
		history.back();
		console.log($posts, posts);
	}

	function back() {
		history.back();
	}
</script>

<h1>Write 라우팅 적용 성공!</h1>
<input bind:value={title} placeholder="제목" />
<input bind:value={content} type="content" name="" id="" placeholder="내용" />

<div>{time.toLocaleDateString()} {time.toLocaleTimeString()}</div>
<button on:click={write}>작성하기</button>

<button on:click={back}>뒤로가기</button>

<style></style>
