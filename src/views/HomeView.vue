<template>
  <input type="text" v-model="ara">
  <div v-for="isim in bulunanlar" :key="isim">
    {{ isim }}
  </div>
</template>

<script>
import { ref, computed, watch, watchEffect } from "vue";

export default {
  name: "HomeView",
  setup() {
    const isimler = ref(["Luffy", "Zoro", "Nami", "Sanji", "Usop"]);
    let ara = ref('');

    const bulunanlar = computed(() => {
      return isimler.value.filter((isim) => isim.includes(ara.value));
    });

    watch(ara, () => {
      console.log('watch çalıştı'); // Sadece belirtilen source'da değişiklik kontrolü(dinlemesi) yapıyor.
    });

    watchEffect(() => {
      console.log('watchEffect çalıştı!', isimler.value); // Birden fazla değişiklik kontrolü(dinlemesi) yapabiliyor.
      console.log('watchEffect çalıştı!', ara.value);
    })

    return { isimler, bulunanlar, ara };
  },
};
</script>
