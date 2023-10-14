<template>
  <div>
    <NavBar />
    <h1>Vista Categorías</h1>
    <Notificacion />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Notificacion from '~/components/Notificacion.vue'
export default {
  // Nombre del componente
  name: 'Categorias',

  // Componentes importados
  components: { NavBar, Notificacion },
}
</script>

<style scoped></style>
