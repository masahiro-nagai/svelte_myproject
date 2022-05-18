<script>
let showModal = true
    export let people = [
            { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
            { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
            { name: 'luigi', beltColour: 'brown', age: 35, id: 3 },
        ]
    const handleClick = (id) =>{
		people = people.filter((person)=> person.id != id)
	}
	let isPromo =true
</script>
{#if showModal}
<div class="backdrop" class:promo={isPromo}>
    <div class="modal">
        <p>Sign up for offers!</p>
    </div>

</div>
{/if}
<main>
	{#each people as person(person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColour === "black"}
			<p><strong>Master Ninja</strong></p>
			{/if}
			<p>{person.age}years old, {person.beltColour} belt.</p>
			<button on:click={()=>{handleClick(person.id)}}>DELETE</button>
		</div>
		{:else}<p>There are no people to show...</p>
	{/each}

</main>
<style>
.backdrop{
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0,0,0,0.8);
}
.modal{
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
}
.promo .modal{
    background: crimson;
    color: white;
}
</style>