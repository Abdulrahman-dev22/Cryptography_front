<template>

  <div class="bg-slate-300 h-screen flex justify-center items-center">

    <div class="bg-white w-[750px] h-[750px] flex flex-col justify-center items-center p-6 shadow-lg rounded-lg space-y-6">

  <h1 class="text-black text-4xl font-bold">Shift Cipher Encryption</h1>

  <input
    v-model="text"
    placeholder="Enter Arabic text"
    class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
  />

  <input
    v-model="shift"
    type="number"
    placeholder="Enter shift value"
    class="border border-gray-300 p-3 w-full rounded-md text-lg focus:outline-none focus:ring-2 focus:ring-emerald-500"
  />
  <div class=" justify-between">
    <button
    @click="encryptShiftCipher"
    class="bg-emerald-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold"
  >
    Encrypt
  </button>

  <button
        @click="decryptShiftCipher"
        class="bg-red-500 text-white py-3 px-6 rounded-md hover:bg-emerald-700 transition-all text-lg font-semibold"
      >
        Decrypt
      </button>
  </div>



  <p class="text-gray-700 text-2xl"> Text: {{ encryptedText || decryptedText  }}</p>
</div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
      shift: 0,
      encryptedText: "",
      decryptedText: "",
    };
  },
  methods: {
    async encryptShiftCipher() {
      try {
        const response = await this.$axios.post("/api/shift-cipher", {
          text: this.text,
          shift: parseInt(this.shift),
        });
        this.encryptedText = response.data.encrypted;
      } catch (error) {
        console.error("Error encrypting shift cipher:", error);
      }
    },
    async decryptShiftCipher() {
      try {
        const response = await this.$axios.post("/api/shift-decipher", {
          text: this.text,
          shift: parseInt(this.shift),
        });
        this.decryptedText = response.data.decrypted;
      } catch (error) {
        console.error("Error decrypting shift cipher:", error);
      }
    },
  },
};
</script>
