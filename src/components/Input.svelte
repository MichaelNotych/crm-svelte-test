<script lang="ts">
	import type { ChangeEventHandler } from "svelte/elements";

	export let label: string = '';
	export let id: string = '';
	export let value: string = '';
	export let placeholder: string = '';
	export let onChange: ChangeEventHandler<HTMLInputElement> = () => {};
	export let onSubmit: ChangeEventHandler<HTMLInputElement> = () => {};
</script>

<div class="wrapper">
	<label for={id}>{label}</label>
	<input id={id} type="text" bind:value on:change={onChange} on:submit={onSubmit} placeholder={placeholder} />
</div>

<style lang="sass">
	.wrapper 
		width: 100%

	label 
		font-size: 14px
		text-transform: uppercase
		opacity: 0.6
	

	input 
		width: 100%
		padding: 10px 0
		margin-bottom: 20px
		border: none
		font: inherit
		border-bottom: 1px solid rgba(51, 51, 51, 0.3)
		outline: none
		font-size: 20px

		&::placeholder
			font: inherit
			opacity: 0.5
</style>