<template>
  <div class="row row-cols-1 row-cols-md-5 g-4">
    <div class="col" v-for="person in persons" :key="person.id">
      <div class="card h-100">
        <img :src="getAvatar(person)" class="card-img-top" :alt="person.firstName + ' ' + person.lastName">
        <div class="card-body">
          <h5 class="card-title">{{ person.firstName }} {{ person.lastName }}</h5>
          <p class="card-text">
            {{ person.firstName }} {{ person.lastName }} ist {{ person.gender === 'MALE' ? 'männlich' : (person.gender === 'FEMALE' ? 'weiblich' : 'divers') }}
            und besitzt
            {{ person.recipes.length }} Rezepte.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PersonsCardList',
  props: {
    persons: {
      type: Array,
      required: true
    }
  },
  methods: {
    getAvatar (person) {
      if (person.gender === 'MALE') {
        return require('../assets/man.png')
      } else if (person.gender === 'FEMALE') {
        return require('../assets/woman.png')
      } else if (person.gender === 'DIVERSE') {
        return require('../assets/diverse.png')
      }
    }
  }
}
</script>

<style scoped>

</style>
