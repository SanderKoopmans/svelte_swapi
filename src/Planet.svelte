<script>
    export let homeworld;
    const planet = (async () => {
    const response = await fetch({homeworld})
    return await response.json();
  })();
</script>

<style></style>

{#await planet}
  <p>Finding the home planet</p>
{:then data} 
  <p>{data.name}</p>
{/await}
<a href={homeworld}>Homeworld</a>