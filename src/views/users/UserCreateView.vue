<script>
import axios from "axios";

export default {
  name: "UserCreateView",
  data() {
    return {
      model: {
        user: {
          firstName: '',
          lastName: '',
          username:'',
          password:'',
          email: '',
          age: '',
          birthDay: ''
        }
      }
    }
  },
  methods: {
    saveUser() {
      axios.post('http://localhost:8080/v1/users', this.model.user)
          .then(res => {
            alert('EL usuario se guardó satisfactoriamente');
            this.model.user = {
                firstName: '',
                lastName: '',
                username:'',
                password:'',
                email: '',
                age: '',
                birthDay: ''
            }
          }).catch(function (error) {
            // hangle error on UI site
      })
    }
  }
}
</script>

<template>
  <div class="container mt-5">
    <div class="card">
      <div class="card-header">
        <h4>Adicionar usuario</h4>
      </div>
      <div class="card-body">
        <div class="mb-3">
          <label for="">Primer nombre</label>
          <input type="text" v-model="model.user.firstName" class="form-control">
        </div>
        <div class="mb-3">
          <label for="">Segundo nombre</label>
          <input type="text" v-model="model.user.lastName" class="form-control">
        </div>
        <div class="mb-3">
          <label for="">Nombre de usuario</label>
          <input type="text" v-model="model.user.username" class="form-control">
        </div>
        <div class="mb-3">
          <label for="">Contraseña</label>
          <input type="password" v-model="model.user.password" class="form-control">
        </div>
        <div class="mb-3">
          <label for="">Correo</label>
          <input type="email" v-model="model.user.email" class="form-control">
        </div>
        <div class="mb-3">
          <label for="">Edad</label>
          <input type="number" v-model="model.user.age" class="form-control">
        </div>
        <div class="mb-3">
          <label for="">Fecha de nacimiento</label>
          <input type="date" v-model="model.user.birthDay" class="form-control">
        </div>
        <div class="mb-3">
          <button type="button" @click="saveUser" class="btn btn-primary">
            Guardar
          </button>&nbsp;
          <RouterLink to="/users" class="btn btn-primary">
            Retornar
          </RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>