<template>
  <div class="home">
    <p>Todo App</p> <br>
    <div v-for="yap in yapilacaklar" :key="yap.id">
      <Yapilacaklar :yapilacak="yap" @sil="silHandle" @update="updateHandle"/>
    </div>
  </div>
</template>

<script>
import Yapilacaklar from '@/components/Yapilacaklar.vue'

export default {
  components: {
    Yapilacaklar
  },
  name: 'Home',
  data() {
    return {
      yapilacaklar: []
    }
  },
  mounted() {
    fetch('http://localhost:3000/yapilacaklar').then((result) => result.json()).then((res) => {
      this.yapilacaklar = res
    }).catch((err) => {
      console.log(err);
    })
  },
  methods: {
    silHandle(id) {
      this.yapilacaklar = this.yapilacaklar.filter((yap) => {
        return yap.id !== id 
      })
    },
    updateHandle(id) {
      let yap = this.yapilacaklar.find((yapilacak) => {
        return yapilacak.id==id
      });
      yap.yapildi =! yap.yapildi;
    }
  },
}
</script>
