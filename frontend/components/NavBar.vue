<template>
  <div>
    <div class="padre">
      <div class="logo"><img src="@/static/logo-sulab.png" alt="Logo" /></div>
      <a href="/productos">Productos</a>
      <a href="/categorias">Categorías</a>
      <a href="/movimientos">Movimientos</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
}
</script>

<style scoped>
/*
  Paleta de colores:
  https://coolors.co/5ab037-211a1d-6320ee-fcfcfc-f7567c
 */
.padre {
  background-color: rgb(42, 184, 116);
  display: flex;
  justify-content: space-around;
}
a {
  text-decoration: none;
  color: black;
  font-size: 24px;
  margin-top: 10px;
}
.logo img {
  height: 60px;
  width: auto;
  margin-right: 50px;
  margin-top: 10px;
  margin-bottom: 10px;
}
/* Cambia el tamaño de la imagen para tamaños de pantalla más pequeños */
@media (max-width: 768px) {
  .logo img {
    height: 30px;
  }
  a {
    font-size: 18px;
  }
}
</style>
