<script>
import sourceData from '@/data.json'

export default {
  props:{
    id: {type: Number, required: true},
  },
  computed: {
    /*destinationId() {
      return parseInt(this.$route.params.id);
    },*/
    destination() {
      return sourceData.destinations.find(destination => destination.id === this.id)
    }
  },
  /*{methods:{
    async initData(){
      const response = await fetch(`/api/${this.$route.params.slug}.json`);
      const data = await response.json();
      this.destination = data;
    }
  },
  async created() {
    this.initData()
    /!*this.$watch(() => this.$route.params, this.initData())*!/
  }}*/
}
</script>

<template>
  <section v-if="destination" class="destination">
    <h1>{{ destination.name }}</h1>
    <div class="destination-details">
      <img :src="`/images/${destination.image}`" :alt="destination.name">
      <p>{{ destination.description }}</p>
    </div>
  </section>
</template>

<style scoped>

</style>