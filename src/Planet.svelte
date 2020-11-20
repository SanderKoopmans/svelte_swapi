<script>
    const planet = (async () => {
    const response = await fetch(`https://swapi.dev/api/planet/${id}`)
    return await response.json();
  })();
</script>

<style></style>

{#await planet}
  <p>Finding the home planet</p>
{:then data} 
  <p>{data.name}</p>
{/await}
<p>Planet</p>