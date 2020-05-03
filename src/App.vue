
<template>
  <div id="app" class="small-container">
    <nav-bar />

    <h1 id="head">Employee</h1>

    <employee-form @add:employee="addEmployee" />
    <employee-table :employees="employees" />
  </div>
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeForm from "@/components/EmployeeForm.vue";
import NavBar from "@/components/NavBar.vue";
export default {
  name: "app",
  components: {
    EmployeeTable,
    EmployeeForm,
    NavBar
  },
  data() {
    return {
      employees: []
    };
  },
  methods: {
    addEmployee(employee) {
      const lastId =
        this.employees.length > 0
          ? this.employees[this.employees.length - 1].id
          : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };
      this.employees = [...this.employees, newEmployee];
    }
  }
};
</script>

<style>
button {
  background: green;
  border: 1px solid darkred;
}

.small-container {
  max-width: 680px;
}
</style>
