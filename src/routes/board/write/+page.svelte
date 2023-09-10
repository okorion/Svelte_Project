<script>
	let title;
	let content;
	let time = new Date();

	function updateTime() {
		time = new Date();
	}

	// 매 초마다 시간 업데이트
	const interval = setInterval(updateTime, 1000);

	function write() {
		alert('작성완료');
		history.back();
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
