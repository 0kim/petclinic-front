<template>
  <div>
    <h1>AK 직원 소개</h1>

    <div v-for="vet in vets">
      <h2>{{vet.lastName}}{{vet.firstName}}</h2>
      {{vet.description}}
      <div class="special-tag">
        <code>"{{vet.year}}년차"</code>
        <code v-for="specialty in vet.specialties">"{{specialty.name}}"</code>
      </div>
    </div>

  </div>
</template>

<script>
import restService from '../services/restService'
export default {
  name: 'Staffs',
  data: function() {
    return {
      vets : []
    }
  },
  created () {
    restService.fetchVets().then(r => {console.log(r); this.vets = r})
  }
}
</script>

<style scoped>

</style>
