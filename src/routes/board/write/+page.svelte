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
<input bind:value={title} type="title" placeholder="제목" />
<input bind:value={content} type="text" name="" id="" placeholder="내용을 입력해주세요." />

<div>{time.toLocaleDateString()} {time.toLocaleTimeString()}</div>
<button on:click={write}>작성하기</button>

<button on:click={back}>뒤로가기</button>

<style>
	input[type='title'] {
		height: 2rem; /* 원하는 높이로 조절하세요 */
		padding: 0px 6px;
	}

	input[type='text'] {
		height: 20rem; /* 원하는 높이로 조절하세요 */
		text-align: top;
		vertical-align: top;
		padding: 5px 6px;
	}

	input[type='text']::placeholder {
		font-size: 1rem;
	}
</style>
