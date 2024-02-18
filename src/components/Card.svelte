<script>
  import { Card, Button, Rating, Badge } from "flowbite-svelte";
  export let image;
  export let title;
  export let price;
  export let rating;
  export let id;

  $: href = `product/${id}`;
</script>

<Card padding="none">
  <a {href} class="flex justify-center">
    <img
      class="p-8 rounded-t-lg w-full h-[400px] object-contain"
      src={image}
      alt={title}
    />
  </a>
  <div class="px-5 pb-5">
    <a href="/">
      <h5
        class="text-xl font-semibold tracking-tight text-gray-900 dark:text-white truncate"
      >
        {title}
      </h5>
    </a>
    <Rating rating={rating.rate} size="24" class="mt-2.5 mb-5">
      <Badge slot="text" class="ms-3">{rating.rate}</Badge>
    </Rating>
    <div class="flex justify-between items-center">
      <span class="text-3xl font-bold text-gray-900 dark:text-white"
        >$ {price}</span
      >
      <Button href="/">Buy now</Button>
    </div>
  </div>
</Card>
