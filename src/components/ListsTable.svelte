<script lang="ts">
	import type { ListRow } from "../types";

	export let listArr:Array<ListRow> = [];
	export let listHeader:Array<string> = [];
</script>

<section class="list">
	<ul class="list__header">
		{#each listHeader as col}
			<li class="list__col">
				{col}
			</li>
		{/each}
	</ul>
	<ul class="list__content">
		{#each listArr as list}
			<li class="list__item">
				<div class="list__col list__col_name">
					<a href="/">{list.name}</a>
				</div>
				<div class="list__col">
					{list.lastLead || 'no leads yet'}
				</div>
				<div class="list__col">
					{list.leads}
				</div>
			</li>
		{/each}
	</ul>
</section>

<style lang="sass">
	.list
		display: flex
		flex-direction: column
		align-items: center
		justify-content: center
		border-radius: 3px
		background-color: #fff

		&__header
			display: flex
			width: 100%
			padding: 20px
			border-bottom: 1px solid rgba(51, 51, 51, 0.3)

			li
				font-size: 14px
				line-height: 1
				text-transform: uppercase
				opacity: 0.6


		&__col
			flex-basis: auto

			&_name
				font-size: 20px

			&:nth-child(1)
				flex-basis: 60%

			&:nth-child(2),
			&:nth-child(3)
				flex-basis: 20%

		&__content
			width: 100%

		&__item
			display: flex
			align-items: baseline
			width: 100%
			padding: 20px
			transition: background-color

			&:not(:last-child)
				border-bottom: 1px solid rgba(51, 51, 51, 0.3)
</style>