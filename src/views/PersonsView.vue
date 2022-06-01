<template>
  <div class="row row-cols-1 row-cols-md-2 g-4">
    <div class="col" v-for="person in persons" :key="person.id">
      <div class="card">
        <img :src="getAvatar(person)" class="card-img-top" :alt="person.firstName + ' ' + person.lastName">
        <div class="card-body">
          <h5 class="card-title">{{ `${person.firstName} ${person.lastName}` }}</h5>
          <p class="card-text">
            {{ `${person.firstName} ${person.lastName}` }} ist {{ person.gender === 'MALE' ? 'männlich' : 'weiblich' }} und besitzt
            {{ person.recipe.length }} Rezepte
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PersonsView',
  data () {
    return {
      persons: [
        {
          id: 1,
          firstName: 'Max',
          lastName: 'Mustermann',
          gender: 'MALE',
          recipe: []
        },
        {
          id: 2,
          firstName: 'Maia',
          lastName: 'Hedwig',
          gender: 'FEMALE',
          recipe: []
        }
      ]
    }
  },
  methods: {
    getAvatar (person) {
      if (person.gender === 'MALE') {
        return require('../assets/man.png')
      } else if (person.gender === 'FEMALE') {
        return require('../assets/woman.png')
      }
    }
  }
}
</script>

<style scoped>

</style>
