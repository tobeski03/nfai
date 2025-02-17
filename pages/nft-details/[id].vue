<script setup>
import { useRoute } from "vue-router";

const route = useRoute();
const nft = {
  image: route.query.image,
  title: route.query.title,
  price: route.query.price,
  creator: route.query.creator,
};
</script>

<template>
  <div class="bg-black text-white p-6">
    <!-- NFT Display Section -->
    <div class="flex flex-row gap-10">
      <!-- NFT Image -->
      <div class="flex justify-center">
        <img :src="nft.image" alt="NFT Image" class="w-full max-w-md rounded-lg shadow-lg" />
      </div>

      <!-- NFT Details -->
      <div class="space-y-6">
        <h1 class="text-3xl font-bold">{{ nft.title }}</h1>

        <div class="flex items-center space-x-2 text-gray-400">
          <img
            src="https://loremflickr.com/40/40/avatar"
            alt="Creator Avatar"
            class="w-8 h-8 rounded-full"
          />
          <span>{{ nft.creator }}</span>
        </div>

        <p class="mt-4 bg-gray-700 px-4 py-2 rounded-md text-yellow-400 text-sm">
          Item not listed yet
        </p>

        <div>
          <input
            type="text"
            placeholder="List price (ETH)"
            class="w-full bg-gray-800 px-4 py-2 rounded-md text-white"
          />
        </div>

        <button class="mt-4 w-full bg-yellow-400 text-black py-2 rounded-md font-semibold">
          Buy now
        </button>

        <p class="text-gray-400 text-xs mt-2">
          By clicking "List now" you agree to Trayde’s
          <a href="#" class="text-yellow-400">Terms and Conditions</a>.
        </p>
      </div>
    </div>

    <!-- Price & Details Section -->
    <div class="mt-8 grid grid-cols-1 md:grid-cols-2 gap-6 bg-gray-900 p-6 rounded-lg">
      <!-- Price History Chart -->
      <div>
        <h2 class="text-lg font-semibold">Price History</h2>
        <div class="bg-gray-800 p-4 rounded-lg h-40 flex items-center justify-center text-xl">
          📈 (Graph Placeholder)
        </div>
      </div>

      <!-- Details -->
      <div>
        <h2 class="text-lg font-semibold">Details</h2>
        <div class="bg-gray-800 p-4 rounded-lg">
          <p class="text-gray-400">Token Address</p>
          <p class="text-white">0xbd...2cf8</p>

          <p class="text-gray-400 mt-2">Owner</p>
          <p class="text-white">0xbd...2cf8</p>

          <p class="text-gray-400 mt-2">Artist Royalties</p>
          <p class="text-white">6%</p>

          <p class="text-gray-400 mt-2">Transaction Fee</p>
          <p class="text-white">2%</p>
        </div>
      </div>
    </div>

    <!-- About Section -->
    <div class="mt-8 bg-gray-900 p-6 rounded-lg">
      <h2 class="text-lg font-semibold">About the Collection</h2>
      <div class="flex items-center space-x-3 mt-3">
        <img
          src="https://loremflickr.com/40/40/avatar"
          alt="Project Avatar"
          class="w-10 h-10 rounded-full"
        />
        <p class="text-gray-400 text-sm">
          Pudgy Penguins is a collection of 8888 NFTs, accelerating Web3 innovation through IP
          utilization and community empowerment. Embodying love, empathy, & compassion...
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
@media (max-width: 768px) {
  .bg-gray-900 {
    background-color: #1f1f1f;
  }

  .text-gray-400 {
    color: #a0a0a0;
  }
}

@media (min-width: 1024px) {
  .bg-black {
    background-color: #121212;
  }
}
</style>
