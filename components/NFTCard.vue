<script>
export default {
  props: {
    image: String,
    title: String,
    price: String,
    creator: String,
  },
};
</script>

<template>
  <div class="bg-gray-800 p-4 rounded-lg">
    <img :src="image" alt="NFT Image" class="w-full h-40 object-cover rounded-md" />
    <h3 class="text-white font-bold mt-2">{{ title }}</h3>
    <p class="text-gray-400 text-sm">{{ creator }}</p>
    <div class="flex justify-between items-center mt-2">
      <p class="text-yellow-400 font-semibold">{{ price }}</p>
      <button class="bg-yellow-400 text-black px-3 py-1 rounded-md text-sm">Buy</button>
    </div>
  </div>
</template>
