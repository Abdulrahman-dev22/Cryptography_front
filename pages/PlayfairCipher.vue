<template>
  <div class="bg-slate-300 h-screen flex justify-center items-center">
    <div class="bg-white w-[750px] h-[750px] flex flex-col justify-center items-center p-6 shadow-lg rounded-lg space-y-6">
      <h1 class="text-black text-4xl font-bold">Playfair Cipher Encryption</h1>

      <input
        v-model="text"
        placeholder="Enter Arabic text"
        class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
      />

      <input
        v-model="keyword"
        placeholder="Enter keyword"
        class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
      />

      <div class="justify-between">
        <button
          @click="encryptPlayfairCipher"
          class="bg-emerald-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold"
        >
          Encrypt
        </button>

        <button
          @click="decryptPlayfairCipher"
          class="bg-red-500 text-white py-3 px-6 rounded-md hover:bg-red-700 transition-all text-lg font-semibold"
        >
          Decrypt
        </button>
      </div>

      <p class="text-gray-700 text-2xl">Result: {{ encryptedText || decryptedText }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
      keyword: "",
      encryptedText: "",
      decryptedText: "",
    };
  },
  methods: {
    async encryptPlayfairCipher() {
      try {
        const response = await this.$axios.post("/api/playfair-encrypt", {
          text: this.text,
          keyword: this.keyword,
        });
        this.encryptedText = response.data.encrypted;
      } catch (error) {
        console.error("Error encrypting Playfair cipher:", error);
      }
    },
    async decryptPlayfairCipher() {
      try {
        const response = await this.$axios.post("/api/playfair-decrypt", {
          text: this.text,
          keyword: this.keyword,
        });
        this.decryptedText = response.data.decrypted;
      } catch (error) {
        console.error("Error decrypting Playfair cipher:", error);
      }
    },
  },
};
</script>
