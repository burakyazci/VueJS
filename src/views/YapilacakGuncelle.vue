<template>
  <form @submit.prevent="updateFormById">
    <div>
      <label for="baslik">Baslık:</label>
      <input type="text" v-model="baslik" />
    </div>
    <div>
      <label for="baslik">İçerik:</label>
      <input type="text" v-model="icerik" />
    </div>
    <button>Submit</button>
  </form>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
          baslik: "",
          icerik: ""
    };
  },
  methods: {
    updateFormById() {
        fetch("http://localhost:3000/yapilacaklar/" + this.id, {
            method: 'PATCH',
            headers: {'Content-Type': 'application/json'},
            body: JSON.stringify({
                id: this.id,
                baslik: this.baslik,
                icerik: this.icerik
            })
        }).then((result) => {
            this.$router.push('/');
        })
    },
  },
  mounted() {
    fetch("http://localhost:3000/yapilacaklar/" + this.id).then(result => result.json()).then((res) =>{
        this.baslik = res.baslik
        this.icerik = res.icerik
    })
  },
};
</script>

<style></style>
