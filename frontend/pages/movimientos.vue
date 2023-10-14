<template>
  <div>
    <NavBar />
    <h1>Movimientos</h1>
    <div class="contenido">
      <a href="/egreso"
        ><button class="btn btn-primary">Egreso de productos 📦</button></a
      >
      <a><button class="btn btn-success">Ingreso de productos 💲</button></a>
      <a><button class="btn btn-danger">Devolución de productos 🌀</button></a>
    </div>
    <Notificacion />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Notificacion from '~/components/Notificacion.vue'
export default {
  // Nombre del componente
  name: 'Movimientos',

  // Componentes importados
  components: { NavBar, Notificacion },
}
</script>

<style scoped>
h1 {
  text-align: center;
  margin-top: 1vh;
}
.contenido {
  display: flex;
  justify-content: space-around;
  height: 100vh;
}

.contenido a button {
  height: 10vh;
  margin-top: 30vh;
  font-size: 35px;
}
</style>
