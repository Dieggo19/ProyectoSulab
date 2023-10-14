<template>
  <div>
    <NavBar />
    <div class="main">
      <h1>Productos</h1>
      <div class="contenido">
        <!-- Operaciones -->
        <div class="operaciones-div">
          <h2>Operaciones</h2>
          <div class="botones-operaciones">
            <button class="btn btn-success" @click="agregar">➕ Agregar</button>
            <button class="btn btn-primary" @click="agregar">Actualizar</button>
            <button class="btn btn-danger" @click="agregar">Borrar</button>
          </div>
        </div>

        <!-- Tabla de productos -->
        <div class="">
          <!-- Agregar clase tabla con bordes de boostrap -->
          <table class="table table-bordered" id="tablaProductos">
            <!-- Agrega filas randoms -->
            <tr>
              <th>Código</th>
              <th>Nombre</th>
              <th>Categoría</th>
              <th>Stock actual</th>
              <th>Stock mínimo</th>
            </tr>
            <tr
              v-for="p in productos"
              :class="{
                bajoStock: p.stockActual < p.stockMin,
                igualStock: p.stockActual == p.stockMin,
                altoStock: p.stockActual > p.stockMin,
              }"
            >
              <td>{{ p.clave }}</td>
              <td>{{ p.nombre }}</td>
              <td>{{ p.categoria }}</td>
              <td>{{ p.stockActual }}</td>
              <td>{{ p.stockMin }}</td>
            </tr>
          </table>
        </div>

        <!-- Filtros -->
        <div class="operaciones-div">
          <h2>Filtros</h2>
          <div class="botones-filtros">
            <button
              class="btn btn-danger"
              type="button"
              @click="getProductosBajoStock"
            >
              Bajos en stock
            </button>

            <button class="btn btn-primary" @click="getAllProductos">
              Limpiar filtros
            </button>
          </div>
        </div>

        <!-- Botón de notificación -->
        <Notificacion />
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Notificacion from '~/components/Notificacion.vue'
import axios from 'axios'
export default {
  // Nombre del componente
  name: 'Productos',

  // Componentes importados
  components: { NavBar, Notificacion },

  // Variables locales
  data() {
    return {
      // Variables
      productos: [],
    }
  },
  methods: {
    // Funciones
    agregar() {
      console.log('Cargando vistas agregarProducto.vue ...')
      this.$router.push('/agregarProducto')
    },
    async getAllProductos() {
      const respuesta = await axios.get('http://localhost:8081/api/productos')
      console.log(respuesta)
      this.productos = respuesta.data
    },
    async getProductosBajoStock() {
      const respuesta = await axios.get(
        'http://localhost:8081/api/productos/bajo-stock'
      )
      console.log(respuesta)
      this.productos = respuesta.data
    },
  },
  mounted() {
    this.getAllProductos()
  },
}
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.contenido {
  display: flex;
  justify-content: space-around;
}

h1 {
  text-align: center;
  margin: 10px;
}

.notificacion-div {
  /* Posición en pantalla */
  position: fixed;
  top: 90vh;
  right: 2vw;

  /* Acomodar botón al centro */
  display: flex;
  justify-content: center;
  align-items: center;

  /* Estilo */
  background-color: #2ab874;
  height: 75px;
  width: 75px;
  border-radius: 50%;
}

.notificacion-div button {
  font-size: 30px;
}

.operaciones-div {
  background-color: #3affa0;
  height: 50vh;
  width: 15vw;
  color: black;
  border-radius: 30px 30px;
  padding: 1%;
}

.operaciones-div h2 {
  text-align: center;
}

.botones-operaciones {
  height: 100%;
  display: flex;
  /* justify-content: center; */
  align-items: center;
  flex-direction: column;
}

.botones-operaciones button {
  margin-top: 30%;
  width: 150px;
  height: 50px;
}

#tablaProductos tr.igualStock {
  background-color: #a8b82a;
}

#tablaProductos tr.bajoStock {
  color: white;
  background-color: #b82a2f;
}

.botones-filtros {
  height: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

.botones-filtros button {
  width: 150px;
  height: 50px;
  margin: auto;
}
</style>
