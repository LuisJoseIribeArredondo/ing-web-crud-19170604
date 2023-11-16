<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Mis Empleados VueJs" />
    <div class="mb-3">
      <!--Id-->
      <label for="lblIdEmp" class="form-label">Id del Empleado</label>
      <input
        type="text"
        class="form-control inputEmpleado"
        id="inputId"
        placeholder="Id del empleado"
      />
      <hr class="division">
            <!--Nombre-->
      <label for="lblNombreEmp" class="form-label">Nombre del Empleado</label>
      <input
        type="text"
        class="form-control inputEmpleado"
        id="inputNombre"
        placeholder="nombre del empleado"
      />
      <hr class="division">
            <!--Departamento-->
      <label for="lblDepartamentoEmp" class="form-label">Departamento del Empleado</label>
      <input
        type="text"
        class="form-control inputEmpleado"
        id="inputDepartamento"
        placeholder="Departamento del empleado"
      />
      <hr class="division">
            <!--Salario-->
      <label for="lblSalarioEmp" class="form-label">Salario del Empleado</label>
      <input
        type="text"
        class="form-control inputEmpleado"
        id="inputSalario"
        placeholder="Salario del empleado"
      />
      <hr class="division">
            <!--Fecha de contratacion-->
      <label for="lblNombreEmp" class="form-label">Fecha de contratacion</label>
      <input
        type="date"
        class="form-control inputEmpleado"
        id="inputFecha"
      />
      <hr class="division">
            <!--Creado en-->
      <label for="lblNombreEmp" class="form-label">Creado en</label>
      <input
        type="date"
        class="form-control inputEmpleado"
        id="inputCreado"
      />
      <hr class="division">
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
};
</script>
<style>
.inputEmpleado{
  max-width: 470px;
  margin: auto;
  font-size: 1.2rem;
}
.division{
  max-width: 560px;
  margin: auto;
  margin-top: 10px;
  margin-bottom: 10px;
}
</style>