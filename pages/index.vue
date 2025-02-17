<!-- <script>
import NFTCard from "~/components/NFTCard.vue";
import SellerCard from "~/components/SellerCard.vue";

export default {
  components: {
    NFTCard,
    SellerCard,
  },
};
</script> -->

<template>
  <div class="bg-[#0d0d0d] text-white min-h-screen px-6 py-4">
    <!-- Header -->
    <header
      class="flex justify-between items-center py-4 border-b border-gray-700"
    >
      <div class="text-yellow-400 text-lg font-bold">TRXNFT</div>
      <nav class="flex space-x-6">
        <a href="#" class="text-gray-400 hover:text-white">Explore</a>
        <a href="#" class="text-gray-400 hover:text-white">Mint</a>
        <a href="#" class="text-gray-400 hover:text-white">Genesis</a>
      </nav>
      <div class="flex space-x-4 items-center">
        <input
          type="text"
          placeholder="Search"
          class="bg-gray-800 px-3 py-2 rounded-md text-white"
        />
        <button
          @click="openModal"
          class="bg-yellow-400 text-black px-4 py-2 rounded-md"
        >
          Connect wallet
        </button>
      </div>
    </header>

    <!-- Featured Section -->
    <section class="mt-8">
      <h2 class="text-xl font-bold">Featured</h2>
      <div class="grid grid-cols-4 gap-4 mt-4">
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
      <div class="grid grid-cols-6 gap-4 mt-4">
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
      <div class="flex space-x-4 mt-4">
        <SellerCard
          v-for="(seller, index) in topSellers"
          :key="index"
          :image="seller.image"
          :name="seller.name"
          :sales="seller.sales"
        />
      </div>
    </section>

    <div
      v-if="isOpen"
      class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center"
    >
      <div class="bg-gray-900 p-6 rounded-lg w-96 relative">
        <button
          @click="closeModal"
          class="absolute top-2 right-2 text-gray-400 text-xl"
        >
          &times;
        </button>
        <div class="flex justify-center mb-4">
          <img src="https://example.com/avatar1.png" alt="Logo" class="w-8" />
        </div>
        <h2 class="text-white text-lg text-center font-bold">
          Connect a wallet
        </h2>
        <p class="text-gray-400 text-center text-sm mb-4">
          Get started with your Ethereum wallet to perform transactions
        </p>
        <div class="space-y-2">
          <button
            class="flex justify-between items-center bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <span class="flex items-center space-x-3">
              <img
                src="https://example.com/avatar1.png"
                alt="Movement Wallet"
                class="w-6"
              />
              <span>Movement Wallet</span>
            </span>
            <span class="text-yellow-400 text-sm">RECOMMENDED</span>
          </button>
          <button
            class="flex items-center space-x-3 bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <img src="https://example.com/avatar1.png" alt="Metamask" class="w-6" />
            <span>Metamask</span>
          </button>
          <button
            class="flex items-center space-x-3 bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <img src="https://example.com/avatar1.png" alt="Phantom" class="w-6" />
            <span>Phantom</span>
          </button>
          <button
            class="flex items-center space-x-3 bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <img src="https://example.com/avatar1.png" alt="Coinbase" class="w-6" />
            <span>Coinbase</span>
          </button>
        </div>
        <button class="text-gray-400 text-sm mt-4 w-full">
          Show more wallet
        </button>
      </div>
    </div>

    <!-- Footer -->
    <footer class="mt-12 border-t border-gray-700 py-6">
      <div class="flex justify-between text-gray-400 text-sm">
        <div>
          <p>TRXNFT &copy; 2024 All rights reserved</p>
          <p>
            The largest NFT marketplace platform, dive into the world of digital
            collectibles.
          </p>
        </div>
        <div>
          <h3 class="text-white font-bold">Marketplace</h3>
          <ul>
            <li>Games</li>
            <li>Art</li>
            <li>Photography</li>
            <li>Membership</li>
          </ul>
        </div>
        <div>
          <h3 class="text-white font-bold">My Account</h3>
          <ul>
            <li>Profile</li>
            <li>Favorites</li>
            <li>Settings</li>
          </ul>
        </div>
        <div>
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
 methods: {
  openModal() {
    console.log("Open modal clicked!");
    this.isOpen = true;
  },
  closeModal() {
    console.log("Close modal clicked!");
    this.isOpen = false;
  },
},

  components: {
    NFTCard,
    SellerCard,
  },
  data() {
    return {
      isOpen: false,
      featuredNFTs: [
        {
          image: "https://example.com/avatar1.png",
          title: "Golden Dog",
          price: "0.8 ETH",
          creator: "CryptoArtist",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Futuristic City",
          price: "1.2 ETH",
          creator: "DigitalKing",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Space Dream",
          price: "0.5 ETH",
          creator: "ArtGenius",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Neon Portrait",
          price: "0.9 ETH",
          creator: "NFTMaster",
        },
      ],
      exploreNFTs: [
        {
          image: "https://example.com/avatar1.png",
          title: "Alien Explorer",
          price: "0.7 ETH",
          creator: "SpaceArtist",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Cyberpunk Girl",
          price: "1.0 ETH",
          creator: "FutureArt",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Abstract Waves",
          price: "0.6 ETH",
          creator: "CreativeMind",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Starry Night",
          price: "1.3 ETH",
          creator: "ModernVanGogh",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Fantasy Forest",
          price: "0.4 ETH",
          creator: "NatureNFT",
        },
        {
          image: "https://example.com/avatar1.png",
          title: "Colorful Dog",
          price: "1.1 ETH",
          creator: "CryptoArtist",
        },
      ],
      topSellers: [
        { image: "https://example.com/avatar1.png", name: "DefiKing", sales: "120" },
        { image: "https://example.com/avatar1.png", name: "OverseerNFT", sales: "98" },
        { image: "https://example.com/avatar1.png", name: "WonderDeFi", sales: "85" },
        { image: "https://example.com/avatar1.png", name: "Brainiac", sales: "76" },
        { image: "https://example.com/avatar1.png", name: "InnovatorX", sales: "65" },
        { image: "https://example.com/avatar1.png", name: "PixelShade", sales: "54" },
      ],
    };
  },
};
</script>
