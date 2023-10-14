<template>
  <div>
    <NavBar />
    <div class="main">
      <h1>Agregar Producto</h1>
      <div class="contenido">
        <div class="form-principal">
          <form>
            <div class="form-row">
              <div class="form-group col-md-6">
                <label for="nombreProducto">Nombre del producto</label>
                <input
                  v-model="producto.nombre"
                  type="text"
                  class="form-control"
                  id="nombreProducto"
                  name="nombre"
                  placeholder="Ingrese el nombre del producto..."
                />
              </div>
              <div class="form-group col-md-6">
                <label for="fechaVenc">Fecha de vencimiento</label>
                <input
                  v-model="producto.fechaVenc"
                  type="date"
                  class="form-control"
                  id="fechaVenc"
                  name="fechaVenc"
                  placeholder="Ingrese el nombre del producto..."
                />
              </div>
            </div>
            <div class="form-row">
              <div class="form-group col-md-6">
                <label for="categoria">Categoria</label>
                <input
                  v-model="producto.categoria"
                  type="text"
                  class="form-control"
                  id="categoria"
                  name="categoria"
                  placeholder="Ingrese la categoría del producto..."
                />
              </div>
              <div class="form-group col-md-6">
                <label for="clave">Codigo</label>
                <input
                  v-model="producto.clave"
                  type="text"
                  class="form-control"
                  id="clave"
                  name="clave"
                  placeholder="Ingrese la código del producto..."
                />
              </div>
            </div>
            <div class="form-row">
              <div class="form-group col-md-6">
                <label for="stockMinimo">Stock Minimo</label>
                <!-- Agregar valor por defecto cero -->
                <input
                  v-model="producto.stockMin"
                  class="form-control"
                  type="number"
                  value="0"
                  name="stockMin"
                  id="stockMinimo"
                />
              </div>
              <div class="form-group col-md-3">
                <label for="costoUnitario">Costo unitario $</label>
                <!-- Agregar valor por defecto cero -->
                <input
                  v-model="producto.costo"
                  class="form-control"
                  type="number"
                  value="0"
                  name="costo"
                  id="costoUnitario"
                />
              </div>
              <div class="form-group col-md-3">
                <label for="unidadVenta">Unidad venta</label>
                <!-- Agregar valor por defecto cero -->
                <input
                  v-model="producto.unidadVenta"
                  class="form-control"
                  type="number"
                  value="0"
                  name="unidadVenta"
                  id="unidadVenta"
                />
              </div>
            </div>

            <div class="form-row">
              <div class="form-group col-md-6">
                <label for="precioSinIva">Precio sin IVA $</label>
                <!-- Agregar valor por defecto cero -->
                <input
                  v-model="producto.precioSinIva"
                  class="form-control"
                  type="number"
                  value="0"
                  name="precioSinIva"
                  id="precioSinIva"
                />
              </div>
              <div class="form-group col-md-6">
                <label for="precioConIva">Precio con IVA $</label>
                <!-- Agregar valor por defecto cero -->
                <input
                  v-model="producto.precioConIva"
                  class="form-control"
                  type="number"
                  value="0"
                  name="precioConIva"
                  id="precioConIva"
                />
              </div>
            </div>
          </form>
          <div class="d-flex" id="botones-cancelar-agregar">
            <!-- Botón cancelar para llevar a la vista /productos -->
            <a href="/productos">
              <button class="form-control btn btn-danger">Cancelar</button>
            </a>
            <button
              @click="agregarProducto"
              class="form-control btn btn-success"
            >
              Agregar producto
            </button>
          </div>
        </div>

        <Notificacion />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import NavBar from '~/components/NavBar.vue'
import Notificacion from '~/components/Notificacion.vue'

export default {
  name: 'AgregarProducto',
  components: { NavBar, Notificacion },
  data() {
    return {
      producto: {
        clave: '',
        nombre: '',
        fechaVenc: '',
        clave: '',
        categoria: '',
        stockMin: 0,
        costo: 0,
        precioSinIva: 0,
        precioConIva: 0,
        unidadVenta: 0,
      },
    }
  },
  methods: {
    async agregarProducto() {
      const response = await axios.post(
        'http://localhost:8081/api/productos',
        this.producto
      )
      console.log(response)

      this.producto = {
        clave: '',
        nombre: '',
        fechaVenc: '',
        clave: '',
        categoria: '',
        stockMin: 0,
        costo: 0,
        precioSinIva: 0,
        precioConIva: 0,
      }

      response.status === 200 ? alert('Producto agregado correctamente') : null
    },
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
  justify-content: center;
  align-items: center;
  height: 80vh;
}

.form-principal {
  /* background-color: #2ab874; */
  width: 50vw;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  border: 1px solid grey;
  border-radius: 15px 15px;
  padding: 15px;
}

.form-principal input {
  margin-bottom: 25px;
}

h1 {
  text-align: center;
}

#botones-cancelar-agregar a {
  width: 10vw;
}
</style>
