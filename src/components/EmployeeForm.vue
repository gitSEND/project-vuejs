<template>
  <div id="employee-form">
    <form @submit.prevent="handleSubmit">
      <label for="name">Ingrese su nombre</label>
      <input
        ref="first"
        v-model="employee.name"
        :class="{'hass-error':submitting && invalidName}"
        @focus="clearStatus"
        @keypress="clearStatus"
        type="text"
      />

      <label for="correo">Ingrese su correo</label>
      <input
        type="text"
        :class="{ 'has-error': submitting && invalidEmail }"
        v-model="employee.email"
        @focus="clearStatus"
      />
      <p v-if="error && submitting" class="error-message">Por favor debe completar el formulario</p>
      <p v-if="success" class="success-message">Empleado registrado correctamente</p>

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
      this.submitting = true;
      this.clearStatus();
      if (this.invalidName || this.invalidEmail) {
        this.error = true;
        return;
      }
      //this.$emit('name-of-envent',data)
      this.$emit("add:objEmp", this.employee);
      this.$refs.first.focus();
      this.employee = {
        name: "",
        email: ""
      };
      this.error = false;
      this.success = true;
      this.submitting = false;
    },
    clearStatus() {
      this.success = false;
      this.error = false;
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 128px;
}
[class*="-message"] {
  font-weight: 500;
}
.error-message {
  color: rgb(145, 20, 20);
}
.success-message {
  color: rgb(58, 161, 58);
}
</style>