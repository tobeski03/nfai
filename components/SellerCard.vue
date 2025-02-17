<script>
export default {
  props: {
    image: String,
    name: String,
    sales: String,
  },
};
</script>

<template>
  <div class="flex flex-col items-center bg-gray-800 p-4 rounded-lg w-32">
    <img :src="image" alt="Seller Avatar" class="w-16 h-16 object-cover rounded-full border-2 border-yellow-400" />
    <h3 class="text-white font-bold mt-2 text-center">{{ name }}</h3>
    <p class="text-gray-400 text-sm">{{ sales }} Sales</p>
  </div>
</template>
