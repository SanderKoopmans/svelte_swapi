<script>
  import Planet from './Planet.svelte';

  const people = (async () => {
    const response = await fetch('https://swapi.dev/api/people/')
    return await response.json();
  })();

</script>

<style>
  div {
    text-align: center;
    background: #999;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 5px 5px 5px rgba(255, 255, 255, 0.1);
    width: 80%;
    align-self: center;
    margin-bottom: 10px;
  }
</style>

{#await people}
  <p>...looking up characters</p>
  {:then data}
  {#each data.results as person}
<div class="card-person">
  <h2>{person.name}</h2>
  <p>{person.gender}</p>
  <Planet homeworld={person.homeworld} />
</div>
{/each}
{:catch error}
  <p>Something went wrong! {error.message}</p>
{/await}