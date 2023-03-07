<script>
	import Card from './Card.svelte';
	export let item;
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
	const handleDelete = (itemId) => {
		dispatch('deleteItem', itemId);
	};
</script>

<Card>
	<span class="rating">
		{Math.ceil(item.rating / 10)}
	</span>

	<button class="closeBtn" on:click={() => handleDelete(item.id)}> X </button>
	<span class="username">
		{item.user.username}
	</span>
	<p class="body">
		{item.body}
	</p>
</Card>

<style>
	.rating {
		position: absolute;
		width: 50px;
		height: 50px;
		top: -10px;
		left: -10px;
		border: 1px solid #eee;
		border-radius: 50%;
		text-align: center;
		padding: 2px;
		display: grid;
		place-items: center;
		font-size: 19px;

		background-color: rgb(42, 50, 3);
		color: white;
	}
	.closeBtn {
		position: absolute;
		top: 14%;
		right: 4%;
		cursor: pointer;
		border: none;
		background: none;
		color: white;
	}
	.closeBtn:hover {
		opacity: 0.8;
	}
	.username {
		margin-left: 2.2rem;
		font-weight: bold;
		font-size: 1rem;
	}
	.body {
		font-size: 0.9rem;
	}
</style>
