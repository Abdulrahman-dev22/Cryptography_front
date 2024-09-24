<template>
    <div class="bg-slate-300 h-screen flex justify-center items-center">
      <div class="bg-white w-[750px] h-[750px] flex flex-col justify-center items-center p-6 shadow-lg rounded-lg space-y-6">


        <!-- Decryption Section -->
        <h1 class="text-black text-4xl font-bold mt-10">Vigenere Cipher Decryption</h1>
        <input
          v-model="cipherText"
          placeholder="Enter Encrypted text"
          class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
        />
        <input
          v-model="vigenereKey"
          placeholder="Enter key"
          class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
        />
        <button
          @click="decryptVigenereCipher"
          class="bg-emerald-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold"
        >
          Decrypt
        </button>
        <p class="text-gray-700 text-2xl">Decrypted Text: {{ decryptedVigenereText }}</p>
      </div>
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        vigenereText: '',
        vigenereKey: '',
        encryptedVigenereText: '',
        cipherText: '',
        decryptedVigenereText: ''
      };
    },
    methods: {

      async decryptVigenereCipher() {
        try {
          const response = await this.$axios.post('/api/vigenere-decipher', {
            text: this.cipherText,
            key: this.vigenereKey
          });
          this.decryptedVigenereText = response.data.decrypted;
        } catch (error) {
          console.error('Error decrypting Vigenere cipher:', error);
        }
      }
    }
  };
  </script>
