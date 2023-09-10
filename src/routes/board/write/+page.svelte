<script>
	function write() {
		alert("작성완료");
		history.back();
	}
	
	function back() {
		history.back();
	}
</script>

<h1>Write 라우팅 적용 성공!</h1>
<input type="title" placeholder="제목">
<input type="content" name="" id="" placeholder="내용">
<button on:click={write}>작성하기</button>

<button on:click={back}>뒤로가기</button>

<style></style>
