<template>
  <div class="bg-slate-300 h-screen flex flex-col items-center">
    <!-- Header -->
    <div class="bg-emerald-600 w-full h-20 flex items-center justify-between shadow-2xl rounded-b-full px-10">
      <img src="/images/logo.png" alt="" class="h-12 w-13 object-center" />
    </div>

    <!-- Main Content -->
    <div class="mt-16 border border-slate-600 rounded-xl bg-white flex items-center justify-between p-10 w-max shadow-lg">
      <!-- Text Section -->
      <div class="flex flex-col space-y-5">
        <h1 class="font-extrabold text-slate-600 text-5xl">Encryption Tool</h1>
        <h3 class="text-black text-2xl font-thin w-[600px]">
          Explore the world of cryptography with ease, whether you're looking to use a shift cipher, monoalphabetic cipher, or Vigenère cipher.
        </h3>
      </div>

      <!-- Image Section -->
      <div>
        <img src="/images/encryption.png" alt="" class="rounded-xl h-[450px] w-auto shadow-xl" />
      </div>
    </div>

    <!-- Cipher Links -->
    <div class="mt-24 w-full max-w-4xl text-white text-center flex justify-between text-2xl space-x-5">
      <nuxt-link to="ShiftCipher" class="bg-emerald-600 py-3 px-7 rounded-xl hover:bg-emerald-800 transition-all">Shift Cipher</nuxt-link>
      <nuxt-link to="MonoalphabeticCipher" class="bg-emerald-600 py-3 px-7 rounded-xl hover:bg-emerald-800 transition-all">Monoalphabetic Cipher</nuxt-link>
      <nuxt-link to="VigenereCipher" class="bg-emerald-600 py-3 px-7 rounded-xl hover:bg-emerald-800 transition-all">Vigenere Cipher</nuxt-link>
      <nuxt-link to="PlayfairCipher" class="bg-emerald-600 py-3 px-7 rounded-xl hover:bg-emerald-800 transition-all">Playfair Cipher</nuxt-link> <!-- New Playfair Cipher button -->
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
      vigenereText: "",
      vigenereKey: "",
      encryptedVigenereText: "",
      monoText: "",
      encryptedMonoText: "",
      monoKey: "", // To store the generated key for monoalphabetic cipher
    };
  },
  methods: {},
};
</script>