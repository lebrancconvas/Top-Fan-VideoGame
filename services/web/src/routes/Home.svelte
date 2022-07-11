<script lang="ts">
import { onMount } from "svelte";
import axios from 'axios';

let quizes = [];

onMount(async () => {
	const res = await axios.get('http://localhost:9000/quiz');
	quizes = res.data;
});
</script>

<main>
	<header>
		<div>
			<h1>Question</h1>
		</div>
	</header>
	<section class="quiz">
		{#each quizes as quiz}
		<div>
			<h2>{quiz.question}</h2>
			<div class="choice">
				{#each quiz.choices as choice}
					<div>{choice}</div>
				{/each}
			</div>
		</div>
		{/each}
	</section>
</main>