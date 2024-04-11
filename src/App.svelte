<script lang="ts">
	import Button from "./components/Button.svelte";
	import Input from "./components/Input.svelte";
	import ListsTable from "./components/ListsTable.svelte";
	import Popup from "./hoc/popup.svelte";
	import { defaultListArr } from "./mocks";

	let listArr = defaultListArr;
	let creatListPopupIsOpen: boolean = false;
	let createListName: string = '';
	
	function newListNameHandler(e: Event) {
		createListName = (e.target as HTMLInputElement)?.value || '';
	}

	function toggleCreateListFlag() {
		creatListPopupIsOpen = !creatListPopupIsOpen;
	}

	function createNewList(e: Event) {
		listArr = [...listArr, {
			id: `${listArr.length + 1}`,
			name: createListName || `Test list ${listArr.length + 1}`,
			lastLead: '',
			leads: 0,
		}];

		toggleCreateListFlag();
	}
</script>

<main class="crm">
	<div class="crm__container">
		<section class="crm__header">
			<div class="crm_header__title">Lists:</div>
			<Button text="Create new list" color="primary" onClick={toggleCreateListFlag}/>
		</section>
		<ListsTable listArr={listArr} listHeader={['Name', 'Last lead', 'Leads']}/>
	</div>
	{#if creatListPopupIsOpen}
		<Popup title="Create new list" onClose={toggleCreateListFlag}>
			<form on:submit|preventDefault={createNewList}>
				<Input label="title" id="list_name" placeholder="My new list" onChange={newListNameHandler}/>
				<div class="crm_popup__btns">
					<Button text="Cancel" type="button" color="secondary" onClick={toggleCreateListFlag}/>
					<Button text="Create" type="submit" color="primary"/>
				</div>
			</form>
		</Popup>
	{/if}
</main>

<style lang="sass">
	.crm
		position: relative
		height: 100vh
		background-color: #f0f0f0

		&__container
			max-width: 1200px
			margin: 0 auto
			padding: 0 20px

		&__header
			display: flex
			justify-content: space-between
			align-items: baseline
			width: 100%
			padding: 40px 0

		&_header__title
			opacity: 0.6

		&_popup__btns
			width: 100%
			display: flex
			align-items: center
			justify-content: flex-end
			gap: 10px
</style>
