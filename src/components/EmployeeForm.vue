<template>
  <div id="employee-form">
    <form @submit.prevent="handleSubmit">
      <label for="name">Ingrese su nombre</label>
      <input v-model="employee.name" type="text" />
      <label for="correo">Ingrese su correo</label>
      <input v-model="employee.email" type="text" />
      <button>addEmployee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "employee-form",
  data() {
    return {
      submitting: false,
      error: false,
      success: false,
      employee: {
        name: "",
        email: ""
      }
    };
  },
  computed: {
    invalidName() {
      return this.employee.name === "";
    },
    invalidEmail() {
      return this.employee.email === "";
    }
  },
  methods: {
    handleSubmit() {
      //this.$emit('name-of-envent',data)
      this.$emit("add:objEmp", this.employee);
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 128px;
}
</style>