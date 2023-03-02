<script>
    import { onMount } from 'svelte';

    let pokeData

    onMount(async () => {
        try {
            const pokeResponse = await fetch('https://pokeapi.co/api/v2/pokemon/12')
            pokeData = await pokeResponse.json()
            console.log(pokeData)
        } catch(err) {
            console.error(err)
        }
    })
</script>

<main>
    <ul>
        {#if pokeData}
            {#each pokeData.results as pokemon}
            <div class="card w-96 bg-base-100 shadow-xl">
                <figure class="px-10 pt-10">
                  <img src="" alt="pokepic" class="rounded-xl" />
                </figure>
                <div class="card-body items-center text-center">
                  <h2 class="card-title">Shoes!</h2>
                  <p>If a dog chews shoes whose shoes does he choose?</p>
                  <div class="card-actions">
                    <button class="btn btn-primary">Buy Now</button>
                  </div>
                </div>
              </div>
            {/each}
        {/if}
    </ul>
</main>