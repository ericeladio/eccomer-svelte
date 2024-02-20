<script>
  import { Button, Rating, Badge } from "flowbite-svelte";

  export let image;
  export let title;
  export let price;
  export let rating;
  export let description;
  export let category;
  export let id;

  let count = 0;

  function pluss() {
    count += 1;
  }
  function less() {
    count -= 1;
    // if (count < 0) {
    //   count = 0;
    // }
  }
  function buy() {
    console.log(id, category);
  }
</script>

<div class="w-full h-screen flex justify-center mt-[300px] flex-col  lg:mt-0 lg:flex-row  md:">
  <div class="grow  flex justify-center items-center" >
    <img class="h-[500px] min-w-[300px] object-contain" src={image} alt="product 1 " />
  </div>
  <div class=" lg:max-w-[500px] mx-5 lg:mx-[200px] flex flex-col justify-center">
    <h5
      class="text-xl font-semibold tracking-tight text-gray-900 dark:text-white mb-[40px] mt-[100px]"
    >
      {title}
    </h5>
    <p class="text-xl tracking-tight text-gray-900 dark:text-white my-[40px]">
      {description}
    </p>
    <Rating rating={rating.rate} size="24" class="mt-2.5 mb-5 my-[10px]">
      <Badge slot="text" class="ms-3">{rating.rate}</Badge>
    </Rating>
    <div class="flex items-center gap-4 mt-[40px]">
      <span class="text-3xl font-bold text-gray-900 dark:text-white flex"
        >$ {price}</span
      >
      <Badge class="ms-3 h-[20px]">50%</Badge>
    </div>
    <div class="flex justify-between items-center my-[80px]">
      <div>
        <Button class="text-xl" on:click={less} disabled={count === 0}>-</Button>
        <span class="mx-3 text-xl">{count}</span>
        <Button class="text-xl" on:click={pluss}>+</Button>
      </div>

      <Button class="text-xl" on:click={buy}>Buy now</Button>
    </div>
  </div>
</div>
