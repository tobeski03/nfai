<template>
  <div class="bg-[#0d0d0d] text-white min-h-screen px-4 sm:px-6 py-4">
    <!-- Header -->
    <header
      class="flex flex-col sm:flex-row justify-between items-center py-4 border-b border-gray-700"
    >
      <div class="text-yellow-400 text-lg font-bold mb-4 sm:mb-0">TRXNFT</div>
      <nav class="flex space-x-4 sm:space-x-6 mb-4 sm:mb-0">
        <a href="#" class="text-gray-400 hover:text-white">Explore</a>
        <a href="#" class="text-gray-400 hover:text-white">Mint</a>
        <a href="#" class="text-gray-400 hover:text-white">Genesis</a>
      </nav>
      <div
        class="flex flex-col sm:flex-row space-y-2 sm:space-y-0 sm:space-x-4 items-center"
      >
        <input
          type="text"
          placeholder="Search"
          class="bg-gray-800 px-3 py-2 rounded-md text-white w-full sm:w-auto"
        />
        <button
          @click="openModal"
          class="bg-yellow-400 text-black px-4 py-2 rounded-md w-full sm:w-auto"
        >
          Connect wallet
        </button>
      </div>
    </header>

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

    <!-- Wallet Modal -->
    <div
      v-if="isOpen"
      class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center"
    >
      <div class="bg-gray-900 p-6 rounded-lg w-11/12 sm:w-96 relative">
        <button
          @click="closeModal"
          class="absolute top-2 right-2 text-gray-400 text-xl"
        >
          &times;
        </button>
        <div class="flex justify-center mb-4">
          <img
            src="https://loremflickr.com/320/240/dog"
            alt="Logo"
            class="w-8"
          />
        </div>
        <h2 class="text-white text-lg text-center font-bold">
          Connect a wallet
        </h2>
        <p class="text-gray-400 text-center text-sm mb-4">
          Get started with your Ethereum wallet to perform transactions
        </p>
        <div class="space-y-2">
          <button
            @click="openSecondPopup"
            class="flex justify-between items-center bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <span class="flex items-center space-x-3">
              <img
                src="https://loremflickr.com/320/240/dog"
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
            <img
              src="https://loremflickr.com/320/240/dog"
              alt="Metamask"
              class="w-6"
            />
            <span>Metamask</span>
          </button>
          <button
            class="flex items-center space-x-3 bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <img
              src="https://loremflickr.com/320/240/dog"
              alt="Phantom"
              class="w-6"
            />
            <span>Phantom</span>
          </button>
          <button
            class="flex items-center space-x-3 bg-gray-800 px-4 py-3 w-full rounded-md text-white"
          >
            <img
              src="https://loremflickr.com/320/240/dog"
              alt="Coinbase"
              class="w-6"
            />
            <span>Coinbase</span>
          </button>
        </div>
        <button class="text-gray-400 text-sm mt-4 w-full">
          Show more wallet
        </button>
      </div>
    </div>

    <div
      v-if="showSecondPopup"
      class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center"
    >
      <div class="bg-gray-800 p-6 rounded-lg shadow-lg w-96 relative">
        <button
          class="absolute top-2 right-2 text-gray-400"
          @click="closePopups"
        >
          ✕
        </button>

        <div class="flex items-center space-x-2 mb-4">
          <div class="w-4 h-4 bg-yellow-400 rounded-full"></div>
          <a
            href="https://trayde.com"
            target="_blank"
            class="text-white text-sm"
            >https://trayde.com</a
          >
        </div>

        <h2 class="text-white text-lg font-semibold mb-2">
          Connect With Movement
        </h2>
        <p class="text-gray-400 text-sm mb-4">
          Select the account(s) to use on this site
        </p>

        <div
          class="bg-gray-700 p-3 rounded-md flex items-center justify-between"
        >
          <label class="flex items-center space-x-2">
            <input
              type="checkbox"
              checked
              class="form-checkbox text-yellow-400"
            />
            <span class="text-white text-sm">Account 1 (0x02da...q12sd)</span>
          </label>
          <span class="text-gray-400 text-xs">0 Token</span>
        </div>

        <p class="text-gray-400 text-xs mt-2">
          Only connect with sites you trust.
          <a href="#" class="text-yellow-400">Learn more</a>
        </p>

        <div class="flex justify-between mt-4">
          <button
            class="px-4 py-2 text-gray-400 hover:text-white"
            @click="closePopups"
          >
            Cancel
          </button>
          <button class="px-4 py-2 bg-yellow-400 text-black rounded-md">
            Next
          </button>
        </div>
      </div>
    </div>

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
    openModal() {
      this.isOpen = true;
    },
    closeModal() {
      this.isOpen = false;
    },
  },
};
</script>
<script setup>
import { ref } from "vue";

// State to control popups
const showFirstPopup = ref(true);
const showSecondPopup = ref(false);

// Open second popup when button is clicked
const openSecondPopup = () => {
  showSecondPopup.value = true;
};

// Close popups
const closePopups = () => {
  showSecondPopup.value = false;
  showFirstPopup.value = false;
};
</script>