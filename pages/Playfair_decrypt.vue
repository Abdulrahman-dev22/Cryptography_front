<template>
  <div class="bg-slate-300 h-screen flex justify-center items-center">
    <div class="bg-white w-[750px] h-[750px] flex flex-col justify-center items-center p-6 shadow-lg rounded-lg space-y-6">
      <h1 class="text-black text-4xl font-bold mt-8">Playfair Cipher Decryption</h1>
      
      <input 
        class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500" 
        v-model="decryptedText" 
        placeholder="Enter Encrypted text" 
      />
      
      <input 
        class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500" 
        v-model="keywordInput" 
        placeholder="Enter Decryption Keyword" 
      />

      <button 
        class="bg-emerald-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold" 
        @click="decryptPlayfairCipher"
      >
        Decrypt
      </button>

      <p class="text-gray-700 text-2xl">Decrypted Text: {{ decryptedPlayfairText }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      decryptedText: '',
      keywordInput: '',
      decryptedPlayfairText: ''
    };
  },
  methods: {
    async decryptPlayfairCipher() {
      try {
        const response = await this.$axios.post('/api/playfair-decrypt', {
          text: this.decryptedText,
          keyword: this.keywordInput
        });
        this.decryptedPlayfairText = response.data.decrypted;
      } catch (error) {
        console.error('Error decrypting Playfair cipher:', error);
      }
    }
  }
};
</script>
