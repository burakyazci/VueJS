<template>
  <div>
    <h1>{{ yapilacak.baslik }}</h1>
    <p>{{ yapilacak.icerik }}</p>
    <router-link :to="{name: 'YapilacakGuncelle', params: {id: yapilacak.id}}"></router-link>
    <button @click="updateForm">Düzenle</button>
    <button @click="yapilacakSil">Sil</button>
    <button @click="yapildiToggle">Yapildi</button>
  </div>
</template>

<script>
export default {
    props:['yapilacak'],
    data() {
        return {
            uri: 'http://localhost:3000/yapilacaklar/' + this.yapilacak.id
        }
    },
    methods: {
        yapilacakSil() {
            fetch(this.uri,{method:'DELETE'})
            .then(() => this.$emit('sil',this.yapilacak.id))
            .catch((err) => {console.log(err);})
        },
        yapildiToggle() {
            fetch(this.uri, {method:'PATCH',
            headers: {'Content-Type': "application/json"},
            body: JSON.stringify({yapildi: !this.yapilacak.yapildi})})
            .then(() => this.$emit('update', this.yapilacak.id))
            .catch((err) => console.log(err));
        },
        updateForm() {
            console.log(this.yapilacak.id);
            this.$emit('updateTest', this.yapilacak.id);
            this.$router.push('/yapilacak-guncelle');
        }
    },
}
</script>

<style></style>
