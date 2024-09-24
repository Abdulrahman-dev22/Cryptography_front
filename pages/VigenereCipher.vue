<template>
    <div class="bg-slate-300 h-screen flex justify-center items-center">
      <div class="bg-white w-[750px] h-[750px] flex flex-col justify-center items-center p-6 shadow-lg rounded-lg space-y-6">
        <h1 class="text-black text-4xl font-bold">Vigenere Cipher Encryption</h1>
        <input class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500" v-model="vigenereText" placeholder="Enter Arabic text" />
        <input class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500" v-model="vigenereKey" placeholder="Enter key" />
        <div class="justify-between">
          <button class="bg-emerald-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold" @click="encryptVigenereCipher">Encrypt</button>
       <nuxt-link to="Vigenere_decrypt"> <button class="bg-red-500 text-white py-3 px-6 rounded-md hover:bg-red-700 transition-all text-lg font-semibold" >Decrypt</button>
        </nuxt-link>
        </div>

        <p class="text-gray-700 text-2xl">Encrypted Text: {{ encryptedVigenereText }}</p>
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
      }
    },
    methods: {
      async encryptVigenereCipher() {
      try {
        const response = await this.$axios.post('/api/vigenere-cipher', {
          text: this.vigenereText,
          key: this.vigenereKey
        });
        this.encryptedVigenereText = response.data.encrypted;
      } catch (error) {
        console.error('Error encrypting Vigenere cipher:', error);
      }
    }
    },
  }
  </script>
