<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Mis Empleados VueJs" />
    
    <div>
      

      <ModalComp/>
    </div>
    
    <!--<h5>{{ miEmpleado }}</h5>-->
    <!--<svg xmlns="http://www.w3.org/2000/svg" style="display: none;">
      <symbol id="info-fill" fill="currentColor" viewBox="0 0 16 16">
        <path d="M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16zm.93-9.412-1 4.705c-.07.34.029.533.304.533.194 0 .487-.07.686-.246l-.088.416c-.287.346-.92.598-1.465.598-.703 0-1.002-.422-.808-1.319l.738-3.468c.064-.293.006-.399-.287-.47l-.451-.081.082-.381 2.29-.287zM8 5.5a1 1 0 1 1 0-2 1 1 0 0 1 0 2z"/>
      </symbol>
    </svg>
    <div class="alert alert-success d-flex align-items-center alerta" role="alert">
      </div>-->
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import ModalComp from "@/components/ModalComp.vue";

export default {
  name: "HomeView",
  components: {
    ModalComp,
    HelloWorld,

  },
  data() {
    return {
      /*empleados: [],
      miEmpleado: {
        id: "",
        nombre: "",
        departamento: "",
        salario: "",
        fecha: "",
        creado: "",
      },*/
      mostrarModal: false,
    };
  },
  methods: {


    agregarEmpleado() {
      if (
        this.miEmpleado.id &&
        this.miEmpleado.nombre &&
        this.miEmpleado.departamento &&
        this.miEmpleado.salario &&
        this.miEmpleado.fecha &&
        this.miEmpleado.creado
      ) {
        // Agregar el objeto al arreglo empleados
        this.empleados.push({ ...this.miEmpleado });

        // Guardar empleados en localStorage
        localStorage.setItem('empleados', JSON.stringify(this.empleados));

        // Limpiar el objeto miEmpleado después de agregarlo
        this.miEmpleado.id = "";
        this.miEmpleado.nombre = "";
        this.miEmpleado.departamento = "";
        this.miEmpleado.salario = "";
        this.miEmpleado.fecha = "";
        this.miEmpleado.creado = "";
        alert("Empleado agregado con exito!!!");
      } else {
        alert(
          "Por favor, complete todos los campos antes de agregar un empleado."
        );
      }
    },
    recuperarEmpleados() {
      // Recuperar empleados del localStorage
      const storedEmpleados = localStorage.getItem('empleados');
      if (storedEmpleados) {
        // Convertir la cadena JSON a un objeto JavaScript y asignar a empleados
        this.empleados = JSON.parse(storedEmpleados);
      }
    },
  },
};
</script>
<style>
.inputEmpleado {
  max-width: 470px;
  margin: auto;
  font-size: 1.2rem;
}
.division {
  max-width: 560px;
  margin: auto;
  margin-top: 10px;
  margin-bottom: 10px;
}

.alerta {
  max-width: 470px;
  margin: auto;
  font-size: 1.2rem;
  margin-top: 15px;
  text-align: center;
}
</style>
