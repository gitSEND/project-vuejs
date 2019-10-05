<template>
  <div id="app" class="small-container">
    <h1>EMPLOYEES</h1>
    <employee-form></employee-form>
    <employee-table :arrEmployees="employees" />
  </div>
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeForm from "@/components/EmployeeForm.vue";

export default {
  name: "app",
  components: {
    EmployeeTable,
    EmployeeForm
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: "Henry",
          email: "hmendo81@gmail.com"
        },
        {
          id: 2,
          name: "Fulano",
          email: "fulano@gmail.com"
        }
      ]
    };
  }
};
</script>

<style scoped>
.small-container {
  max-width: 680px;
}
</style>>


