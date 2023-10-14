<template>
  <div>
    <NavBar />
    <h1>Egreso de producto</h1>
    <div class="wrapper">
      <div class="col-sm-300">
        <!-- Buscador -->
        <div class="search">
          <label for="buscar">Buscar egreso</label>
          <input type="text" v-model="busqueda" placeholder="" />
          <button class="btn btn-dark" @click="buscarEgreso">Buscar</button>
        </div>
        <!-- Tabla de egresos -->
        <div class="table">
          <h3>Ventas realizadas</h3>
          <!-- Agregar tabla con bordes de boostrap -->
          <table class="table table-bordered custom-table" id="tablaEgresos">
            <!-- Columnas -->
            <tr>
              <th>Producto</th>
              <th>Cantidad</th>
            </tr>
            <!--<tr>
            <td>{{ p.producto }}</td>
            <td>{{ p.cantidad }}</td>
          </tr>-->
          </table>
        </div>
      </div>
      <!-- Formulario -->
      <div class="form">
        <div class="form-group col-md-8">
          <label for="rutCliente">RUT</label>
          <input
            type="text"
            id="rutCliente"
            v-model="rut"
            placeholder="RUT del cliente"
          />
        </div>
        <div class="form-group col-md-8">
          <label for="nombreCliente">Nombre</label>
          <input
            type="text"
            id="nombreCliente"
            v-model="nombre"
            placeholder="Nombre del cliente"
          />
        </div>
        <div class="form-group col-md-8">
          <label for="correoCliente">Correo</label>
          <input
            type="text"
            id="correoCliente"
            v-model="correo"
            placeholder="Correo del cliente"
          />
        </div>
        <div class="form-group col-md-8">
          <label for="productoEgreso">Producto</label>
          <!-- Aqui se debe agregar un select con los productos -->
          <select v-model="producto" id="productos">
            <option value="">Seleccionar producto</option>
            <option
              v-for="prod in productos"
              :key="prod.id"
              :value="prod.nombre"
            >
              {{ prod.nombre }}
            </option>
          </select>
        </div>
        <div class="form-group col-md-8">
          <label for="cantidadEgreso">Cantidad</label>
          <input
            type="number"
            id="cantidad"
            v-model="cantidad"
            placeholder="Cantidad vendida"
          />
        </div>
        <div class="form-group col-md-9">
          <label for="fechaEgreso">Fecha</label>
          <input
            v-model="fechaEgreso"
            type="date"
            class="form-control"
            id="fechaEgreso"
            name="fechaEgreso"
          />
        </div>
        <!--Botón para registrar una venta-->
        <div class="form-group col-md-9">
          <button class="btn btn-dark" @click="registrarEgreso">
            Registrar egreso
          </button>
        </div>
      </div>
      <Notificacion />
    </div>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Notificacion from '~/components/Notificacion.vue'
import axios from 'axios'
export default {
  // Nombre del componente
  name: 'Egreso',

  // Componentes importados
  components: { NavBar, Notificacion },

  data() {
    return {
      // Variables
      productos: [],
    }
  },
  methods: {
    buscarEgreso() {},
    registrarEgreso() {},
  },
}
</script>

<style scoped>
h1 {
  text-align: center;
  margin: 10px;
}
h3 {
  margin: 10px;
}
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 5px;
  background-color: rgb(42, 184, 116);
  margin-left: 10%;
  margin-right: 10%;
}
.form {
  grid-column-start: 3;
  grid-column-end: 3;
  margin: 10px;
  margin-left: 50px;
}
/*.form-row {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}*/
.search {
  width: 100%;
  grid-column-start: 1;
  grid-column-end: 3;
  grid-row-start: 1;
  grid-row-end: 1;
  margin: 20px;
}
.table {
  grid-column-start: 1;
  grid-column-end: 3;
  grid-row-start: 2;
  margin: 10px;
}
.custom-table {
  background-color: white;
}
/*.contenido {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80vh;
}*/
</style>
