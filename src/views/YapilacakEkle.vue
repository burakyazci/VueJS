<template>
  <form @submit.prevent="yapilacakEkle">
    <div>
        <label>Başlık:</label>
        <input type="text" v-model="baslik">
    </div>
    <div>
        <label>İcerik:</label>
        <input type="text" v-model="icerik">
    </div>
    <button>Ekle</button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            baslik: '',
            icerik: ''
        }
    },
    methods: {
        yapilacakEkle() {
            let yapilacak = {
                id: Math.floor(Math.random()*100000),
                baslik: this.baslik,
                icerik: this.icerik,
                yapildi: false
            };

            fetch('http://localhost:3000/yapilacaklar', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(yapilacak)
        }).then(() => {this.$router.push('/')})
        .catch((err) => console.log(err))
        }
    },
}
</script>

<style>

</style>