<template>
  <div class="bg-[#0d0d0d] text-white min-h-screen px-4 sm:px-6 py-4">
    <!-- Header -->
    <div class="bg-black text-white w-full">
    <!-- Navbar -->
    <nav class="flex justify-between items-center px-6 py-3 border-b border-gray-700">
      <!-- Left Side (Logo & Links) -->
      <div class="flex items-center space-x-6">
        <div class="flex items-center space-x-2">
          <img src="https://loremflickr.com/40/40/logo" alt="Trayde Logo" class="w-6" />
          <span class="font-semibold">TRAYDE</span>
        </div>
        <a href="#" class="text-gray-400 hover:text-white">Explore</a>
        <a href="#" class="text-gray-400 hover:text-white">Mint</a>
        <a href="#" class="text-gray-400 hover:text-white flex items-center">
          Generate <span class="ml-1 text-yellow-400">⭐</span>
        </a>
      </div>

      <!-- Center (Search Bar) -->
      <div class="flex-1 mx-8">
        <div class="relative">
          <input
            type="text"
            placeholder="Search"
            class="w-full bg-gray-800 text-gray-300 px-4 py-2 rounded-md pl-10 focus:outline-none"
          />
          <span class="absolute left-3 top-2 text-gray-500">
            🔍
          </span>
        </div>
      </div>

      <!-- Right Side (Balance & Profile) -->
      <div class="flex items-center space-x-4">
        <div class="flex items-center space-x-2 bg-gray-800 px-3 py-2 rounded-md">
          <span>🏠</span>
          <span class="text-gray-300">12.367 ETH</span>
        </div>
        <img
          src="https://loremflickr.com/40/40/avatar"
          alt="Profile"
          class="w-8 h-8 rounded-full border border-gray-600"
        />
      </div>
    </nav>

    <!-- Category Filters -->
    <div class="flex space-x-4 px-6 py-2 border-b border-gray-700 text-sm">
      <button class="bg-gray-700 text-white px-4 py-1 rounded-md">All</button>
      <button class="text-gray-400 hover:text-white">Art</button>
      <button class="text-gray-400 hover:text-white">Photography</button>
      <button class="text-gray-400 hover:text-white">Gaming</button>
      <button class="text-gray-400 hover:text-white">CGI</button>
      <button class="text-gray-400 hover:text-white">Physical products</button>
    </div>
  </div>
    <!-- Featured Section -->
    <section class="mt-8">
      <h2 class="text-xl font-bold">Featured</h2>
      <div
        class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mt-4"
      >
        <NFTCard
          v-for="(nft, index) in featuredNFTs"
          :key="index"
          :image="nft.image"
          :title="nft.title"
          :price="nft.price"
          :creator="nft.creator"
        />
      </div>
    </section>

    <!-- Explore NFTs -->
    <section class="mt-8">
      <h2 class="text-xl font-bold">Explore NFTs</h2>
      <div
        class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-6 gap-4 mt-4"
      >
        <NFTCard
          v-for="(nft, index) in exploreNFTs"
          :key="index"
          :image="nft.image"
          :title="nft.title"
          :price="nft.price"
          :creator="nft.creator"
        />
      </div>
    </section>

    <!-- Top Sellers -->
    <section class="mt-8">
      <h2 class="text-xl font-bold">Top sellers</h2>
      <div class="flex flex-wrap gap-4 mt-4">
        <SellerCard
          v-for="(seller, index) in topSellers"
          :key="index"
          :image="seller.image"
          :name="seller.name"
          :sales="seller.sales"
        />
      </div>
    </section>

   
    <!-- Footer -->
    <footer class="mt-12 border-t border-gray-700 py-6">
      <div
        class="flex flex-col sm:flex-row justify-between text-gray-400 text-sm space-y-6 sm:space-y-0"
      >
        <div class="sm:w-1/4">
          <p>TRXNFT &copy; 2024 All rights reserved</p>
          <p>
            The largest NFT marketplace platform, dive into the world of digital
            collectibles.
          </p>
        </div>
        <div class="sm:w-1/4">
          <h3 class="text-white font-bold">Marketplace</h3>
          <ul>
            <li>Games</li>
            <li>Art</li>
            <li>Photography</li>
            <li>Membership</li>
          </ul>
        </div>
        <div class="sm:w-1/4">
          <h3 class="text-white font-bold">My Account</h3>
          <ul>
            <li>Profile</li>
            <li>Favorites</li>
            <li>Settings</li>
          </ul>
        </div>
        <div class="sm:w-1/4">
          <h3 class="text-white font-bold">Follow</h3>
          <ul>
            <li>Instagram</li>
            <li>Twitter</li>
            <li>Facebook</li>
          </ul>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import NFTCard from "~/components/NFTCard.vue";
import SellerCard from "~/components/SellerCard.vue";

export default {
  components: {
    NFTCard,
    SellerCard,
  },
  data() {
    return {
      isOpen: false,
      featuredNFTs: [
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Golden Dog",
          price: "0.8 ETH",
          creator: "CryptoArtist",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Futuristic City",
          price: "1.2 ETH",
          creator: "DigitalKing",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Space Dream",
          price: "0.5 ETH",
          creator: "ArtGenius",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Neon Portrait",
          price: "0.9 ETH",
          creator: "NFTMaster",
        },
      ],
      exploreNFTs: [
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Alien Explorer",
          price: "0.7 ETH",
          creator: "SpaceArtist",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Cyberpunk Girl",
          price: "1.0 ETH",
          creator: "FutureArt",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Abstract Waves",
          price: "0.6 ETH",
          creator: "CreativeMind",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Starry Night",
          price: "1.3 ETH",
          creator: "ModernVanGogh",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Fantasy Forest",
          price: "0.4 ETH",
          creator: "NatureNFT",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          title: "Colorful Dog",
          price: "1.1 ETH",
          creator: "CryptoArtist",
        },
      ],
      topSellers: [
        {
          image: "https://loremflickr.com/320/240/dog",
          name: "DefiKing",
          sales: "120",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          name: "OverseerNFT",
          sales: "98",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          name: "WonderDeFi",
          sales: "85",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          name: "Brainiac",
          sales: "76",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          name: "InnovatorX",
          sales: "65",
        },
        {
          image: "https://loremflickr.com/320/240/dog",
          name: "PixelShade",
          sales: "54",
        },
      ],
    };
  },
  methods: {
 
  },
};
</script>
