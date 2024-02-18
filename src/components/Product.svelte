<script>
    export let id;
    import Nav from "./Nav.svelte";
    import Detail from "./Detail.svelte";
    import { Spinner } from "flowbite-svelte";

    const fetchImage = (async () => {
        const response = await fetch(`https://fakestoreapi.com/products/${id}`);
        console.log("tessss", response);
        return await response.json();
    })();
</script>

<Nav />

{#await fetchImage}
    <div class="w-full h-screen justify-center flex items-center">
        <Spinner size={20} />
    </div>
{:then data}
    <section class="lg:mt-20 ">
        <section class="mt-20">
            <Detail {...data} />
        </section>
    </section>
{:catch error}
    <p>An error occurred!</p>
{/await}
