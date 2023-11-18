<template>
  <div v-for="employee in employees" :key="employee.id">
    <router-link :to="{name: 'PersonelDetay', params:{id: employee.id}}">
      <p>{{ employee.name }}</p>
      <p>{{ employee.surname }}</p><br>
    </router-link>
  </div>
</template>

<script>
export default {
    data() {
        return {
            employees: [
                {id: 1, name: 'Burak', surname: 'Yazıcı'},
                {id: 2, name: 'Test', surname: 'Karabas'},
                {id: 3, name: 'Test1', surname: 'Patates'},
            ]
        }
    },
}
</script>

<style>

</style>