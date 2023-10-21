<script>
	import Modal from "./Modal.svelte";
	import AddPerson from "./addPerson.svelte";
		
	let showModal = false;	

	let people = [
		{name: "Tsunade", beltColor: "Blue", age: 50, id: 1, skills: ["fighting", "sneaking"]},
		{name: "Jiraiya", beltColor: "Indigo", age: 52, id: 2, skills: ["fighting", "sneaking", "running"]}, 
		{name: "Orochimaru", beltColor: "Violet", age: 52, id: 3, skills: ["sneaking"]}
	];	
	const deletePerson = (id) => {
		people = people.filter((person) => person.id != id);
	};
	function toggleModal() {
		showModal = !showModal;
	}
	const addPerson = (event) => {
		const details = event.detail;
		const newPerson = {name: details.name, beltColor: details.beltColor, age: details.age, id: people.length+1, skills: details.skills};
		people = [newPerson, ...people];
		showModal = false;
	};
</script>
<Modal showModal={showModal} on:click={toggleModal}>
	<AddPerson on:addPerson={addPerson}/>
</Modal>
<main>
	<button on:click={toggleModal}>Open Modal</button>
	{#each people as person}
		<div class="container">
			<h4 class="hide">{person.name}</h4>
			<p class="hide">{person.age} years old, {person.beltColor} belt, skills: {person.skills}</p>
			<div class="center"><button class="delete"  on:click={() => deletePerson(person.id)}>X Delete</button></div>
		</div>
	{:else}
		<p>There is no people to show...</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	.container {
		background-color: rgb(33, 33, 33);
		padding: 5px;
		margin: 5px;
		border: solid gray 2px;
		border-radius: 8px;
		cursor: pointer;
		position: relative;
	}
	.delete {
		position: relative;
		background-color: transparent;
		color: red;
		border: solid gray 2px;
		cursor: pointer;
	}

	button {
		cursor: pointer;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>