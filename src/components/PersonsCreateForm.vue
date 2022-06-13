<template>
  <button class="btn btn-success sticky-button" data-bs-toggle="offcanvas" data-bs-target="#persons-create-offcanvas"
          aria-controls="#persons-create-offcanvas">
    <i class="bi bi-persons-plus-fill"></i>
  </button>
  <div class="offcanvas offcanvas-end" tabindex="-1" id="persons-create-offcanvas" aria-labelledby="offcanvas-label">
    <div class="offcanvas-header">
      <h5 id="offcanvas-label">New Person</h5>
      <button type="button" id="close-offcanvas" class="btn-close text-reset" data-bs-dismiss="offcanvas"
              aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
      <form class="text-start">
        <div class="mb-3">
          <label for="first-name" class="form-label">First name</label>
          <input type="text" class="form-control" id="first-name" v-model="firstName" required>
        </div>
        <div class="mb-3">
          <label for="last-name" class="form-label">Last name</label>
          <input type="text" class="form-control" id="last-name" v-model="lastName" required>
        </div>
        <div class="mb-3">
          <label for="gender" class="form-label">Gender</label>
          <select class="form-select" id="gender" v-model="gender" required>
            <option value="" selected disabled>Choose...</option>
            <option value="MALE">Male</option>
            <option value="FEMALE">Female</option>
            <option value="DIVERSE">Diverse</option>
          </select>
        </div>
        <div class="mt-5">
          <button type="submit" class="btn btn-primary me-3" @click="createPerson">Create</button>
          <button type="reset" class="btn btn-danger">Reset</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PersonsCreateForm',
  data () {
    return {
      firstName: '',
      lastName: '',
      gender: ''
    }
  },
  methods: {
    createPerson () {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/persons'
      const myHeaders = new Headers()
      myHeaders.append('Content-Type', 'application/json')

      const raw = JSON.stringify({
        firstName: this.firstName,
        lastName: this.lastName,
        gender: this.gender
      })

      const requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
      }

      fetch(endpoint, requestOptions)
        .catch(error => console.log('error', error))
    }
  }
}
</script>

<style scoped>
.sticky-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 10px 15px;
  border-radius: 30px;
}

.btn-primary {
 /* background-color: #42b983;
  border-color: #42b983;*/
  border-radius: 30px;
}

.btn-danger {
  border-radius: 30px;
}
</style>
