<script>
     import { Spinner } from 'flowbite-svelte';
    import Nav from "./Nav.svelte";
    import Card from "./Card.svelte";

    const fetchImage = (async () => {
        const response = await fetch("https://fakestoreapi.com/products");

        return await response.json()
        
    })();

</script>

<Nav />
{#await fetchImage}
    <div class="w-full h-screen justify-center flex items-center">
        <Spinner size={20} />
    </div>
{:then data}
    <section class="mt-20 grid grid-cols-1 justify-items-center gap-5 mx-5 md:grid-cols-2 lg:grid-cols-4">
        {#each data as product, index (product.id)}
            <Card
                title={product.title}
                image={product.image}
                price={product.price}
                rating={product.rating}
                id={product.id}
            />
        {/each}
    </section>
{:catch error}
    <p>An error occurred!</p>
{/await}
