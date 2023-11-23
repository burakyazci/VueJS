<template>
  <p>{{ ad }} -- {{ yetenekNesnesi.yetenekAd }}</p>
  <button @click="butonTiklandi">Tıkla</button>
</template>

<script>
// @ is an alias to /src
import {ref, reactive} from 'vue'

export default {
  name: 'HomeView',
  setup() {
    const ad = ref("Luffy");
    let yetenekNesnesi = reactive({yetenekAd: 'lastik'});

    const butonTiklandi = () => {
      ad.value = "DEĞİŞTİ";
      yetenekNesnesi.yetenekAd = "Kılıç"
    }
    return {ad, butonTiklandi, yetenekNesnesi}

  }
}
</script>
