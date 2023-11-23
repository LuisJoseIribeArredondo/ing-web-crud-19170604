<template>
  <div>
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#myModal">
      Agregar Empleado
    </button>

    <div class="modal" tabindex="-1" role="dialog" v-show="mostrar"  id="myModal">
      <div class="modal-dialog modal-dialog-scrollable">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title">Agregar Empleados</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                
            
          </div>
          <div class="modal-body">
            <div class="">
              <!--Id-->
              <label for="lblIdEmp" class="form-label">Id del Empleado</label>
              <input
                type="text"
                class="form-control inputEmpleado"
                id="inputId"
                placeholder="Id del empleado"
                v-model="miEmpleado.id"
              />
              <hr class="division" />
              <!--Nombre-->
              <label for="lblNombreEmp" class="form-label"
                >Nombre del Empleado</label
              >
              <input
                type="text"
                class="form-control inputEmpleado"
                id="inputNombre"
                placeholder="nombre del empleado"
                v-model="miEmpleado.nombre"
              />
              <hr class="division" />
              <!--Departamento-->
              <label for="lblDepartamentoEmp" class="form-label"
                >Departamento del Empleado</label
              >
              <input
                type="text"
                class="form-control inputEmpleado"
                id="inputDepartamento"
                placeholder="Departamento del empleado"
                v-model="miEmpleado.departamento"
              />
              <hr class="division" />
              <!--Salario-->
              <label for="lblSalarioEmp" class="form-label"
                >Salario del Empleado</label
              >
              <input
                type="text"
                class="form-control inputEmpleado"
                id="inputSalario"
                placeholder="Salario del empleado"
                v-model="miEmpleado.salario"
              />
              <hr class="division" />
              <!--Fecha de contratacion-->
              <label for="lblNombreEmp" class="form-label"
                >Fecha de contratacion</label
              >
              <input type="date" class="form-control inputEmpleado" id="inputFecha" v-model="miEmpleado.fecha"/>
              <hr class="division" />
              <!--Creado en-->
              <label for="lblNombreEmp" class="form-label">Creado en</label>
              <input type="date" class="form-control inputEmpleado" id="inputCreado" v-model="miEmpleado.creado"/>
              <hr class="division" />
            </div>
        </div>

          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary" @click="agregarEmpleado"> Guardar</button>
          </div>

        </div>
      </div>
    </div>
    <div class="card-body col d-flex justify-content-center" v-for="(miEmpleado, index) in empleados" :key="index">
    <div class="accordion" id="accordionEmpleados">
  <div class="accordion-item" >
    <h2 class="accordion-header" id="headingOne">
      <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
        -Empleado: {{ miEmpleado.nombre }}
      </button>
    </h2>
    <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionEmpleados">
      <div class="accordion-body text-start">
        <p>ID: {{ miEmpleado.id }}</p> <br>
        <p>Nombre: {{ miEmpleado.nombre }}</p> <br>
        <p>Departamento: {{ miEmpleado.departamento }}</p> <br>
        <p>Salario del empleado: {{ miEmpleado.salario }}</p> <br>
        <p>Fecha de contratacion: {{ miEmpleado.fecha }}</p> <br>
        <p>Fecha de creacion: {{ miEmpleado.creado }}</p> <br>
      </div>
      <button type="button" @click="eliminarEmpleado(index)" class="btn btn-danger btn-sm float-right">
        Eliminar empleado
      </button>
    </div>
  </div>
  </div>

        
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
        mostrar: false,
      empleados: [],
      miEmpleado: {
        id: "",
        nombre: "",
        departamento: "",
        salario: "",
        fecha: "",
        creado: "",
      },
    };
  },
  mounted(){
    this.recuperarEmpleados();
  },
  methods: {
    
    mostrarModal(){
      this.mostrar = true;
    },
    cerrarModal(){
      myModal.toggle()
    },
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
        localStorage.setItem('empleadosTXT', JSON.stringify(this.empleados));

        // Limpiar el objeto miEmpleado después de agregarlo
        this.miEmpleado.id = "";
        this.miEmpleado.nombre = "";
        this.miEmpleado.departamento = "";
        this.miEmpleado.salario = "";
        this.miEmpleado.fecha = "";
        this.miEmpleado.creado = "";
        alert("Empleado agregado con exito!!!");
        this.mostrar= false;
      } else {
        alert(
          "Por favor, complete todos los campos antes de agregar un empleado."
        );
      }
    },
    recuperarEmpleados() {
      // Recuperar empleados del localStorage
      const storedEmpleados = localStorage.getItem('empleadosTXT');
      if (storedEmpleados) {
        // Convertir la cadena JSON a un objeto JavaScript y asignar a empleados
        this.empleados = JSON.parse(storedEmpleados);
      }
    },
    eliminarEmpleado(index){
        this.empleados.splice(index,1);
        localStorage.setItem('empleadosTXT', JSON.stringify(this.empleados));
    }
  },
};
</script>

<style></style>
