<template>
    <div class="bg-slate-300 h-screen flex justify-center items-center">
        <div class="bg-white w-[750px] h-[750px] flex flex-col justify-center items-center p-6 shadow-lg rounded-lg space-y-6">
            <h1 class="text-black text-4xl font-bold mt-8">Monoalphabetic Cipher Decryption</h1>
      <input
        class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
        v-model="decryptedText"
        placeholder="Enter Encrypted text"
      />
      <input
        class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
        v-model="monoKeyInput"
        placeholder="Enter Decryption Key"
      />

      <button
        class="bg-emerald-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold"
        @click="decryptMonoalphabeticCipher"
      >
        Decrypt
      </button>
      <p class="text-gray-700 text-2xl">Decrypted Text: {{ decryptedMonoText }}</p>
        </div>

    </div>


</template>
<script>
export default {
  data() {
    return {

      decryptedText: '',
      monoKeyInput: '',
      decryptedMonoText: '',
    }
  },
  methods: {

    async decryptMonoalphabeticCipher() {
      try {
        const response = await this.$axios.post('/api/monoalphabetic-decipher', {
          ciphertext: this.decryptedText,
          key: this.monoKeyInput
        });
        this.decryptedMonoText = response.data.decrypted;
      } catch (error) {
        console.error('Error decrypting monoalphabetic cipher:', error);
      }
    }
  }
}
</script>
