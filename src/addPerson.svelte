<script>
    import { createEventDispatcher } from "svelte";

    let name;
    let beltColor;
    let age;
    let skills = [];

    let dispatch = createEventDispatcher();

    function handleSubmit() {
        const newPerson = {
            name: name,
            beltColor: beltColor,
            age: age,
            skills: skills,
            id: Math.random()
        }
        dispatch("addPerson", newPerson);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <h3>Add a new person</h3>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="number" placeholder="age" bind:value={age}>

    <select bind:value={beltColor}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="brown">brown</option>
        <option value="white">white</option>
    </select><br> 

    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">running<br>
    <button>Add Person</button>
</form>

<style>
</style>