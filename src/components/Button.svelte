<script lang="ts">
	import type { MouseEventHandler } from "svelte/elements";

	export let text: string;
	export let color: string;
	export let type: "button" | "submit" | "reset" = "button";
	export let onClick: MouseEventHandler<HTMLButtonElement> = () => {};
</script>

<button 
	class="button" 
	type={type} 
	class:button_secondary={color === 'secondary'} 
	class:button_primary={color === 'primary'} 
	on:click={onClick}
>
	{text}
</button>

<style lang="sass">
	.button 
		padding: 10px 30px
		border: none
		border-radius: 3px
		transition: background-color 0.3s, transform 0.3s

		&_primary
			background-color: #ff8562
			color: #fff

			&:hover
				background-color: #ff6a3d

		&_secondary
			background-color: #fff
			border: 1px solid rgba(51, 51, 51, 0.6)
			color: #333

			&:hover
				background-color: #eee

		&:active
			transform: scale(0.95)
</style>