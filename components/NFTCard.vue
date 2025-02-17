<template>
  <div
    class="bg-gray-800 p-4 rounded-lg cursor-pointer hover:shadow-lg transition"
    @click="goToDetails"
  >
    <img :src="image" alt="NFT Image" class="w-full h-40 object-cover rounded-md" />
    <h3 class="mt-2 text-white font-semibold">{{ title }}</h3>
    <p class="text-gray-400 text-sm">{{ creator }}</p>
    <p class="text-yellow-400 text-sm mt-1">{{ price }} ETH</p>
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";

const props = defineProps(["image", "title", "price", "creator"]);
const router = useRouter();

const goToDetails = () => {
  router.push({
    path: `/nft-details/${props.title.replace(/\s+/g, "-").toLowerCase()}`,
    query: {
      image: props.image,
      title: props.title,
      price: props.price,
      creator: props.creator,
    },
  });
};
</script>
