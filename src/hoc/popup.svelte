<script lang="ts">
	export let onClose = () => {};
	export let title = '';
</script>

<div class="popup">
	<div class="popup__inner">
		<button class="popup__close" on:click={onClose}></button>
		<div class="popup__title">{title}</div>
		<div class="popup__body">
			<slot/>
		</div>
	</div>
</div>

<style lang="sass">
	.popup
		position: absolute
		left: 0
		top: 0
		width: 100%
		height: 100%
		background-color: rgba(0, 0, 0, 0.7)
		display: flex
		align-items: flex-start
		justify-content: center
		padding-top: 120px

		&__inner
			position: relative
			width: 700px
			background-color: #fff
			border-radius: 5px
			overflow: hidden
			border: 1xp solid #eee

		&__close
			position: absolute
			right: 10px
			top: 15px
			width: 41px
			height: 41px
			border-radius: 3px
			transition: transform 0.3s

			&:hover 
				transform: scale(1.1)

			&::before,
			&::after 
				content: ''
				position: absolute
				top: 20px
				left: 10px
				width: 20px
				height: 1px
				background-color: #333

			&::before
				transform: rotate(45deg)

			&::after
				transform: rotate(-45deg)

		&__title
			font-size: 20px
			padding: 20px
			background-color: #f9f9f9
			border-bottom: 1px solid #eee

		&__body
			padding: 20px

		&__btns
			padding: 0 20px 20px
</style>