<template>
  <div>
    <!-- Botón de notificación -->
    <div class="notificacion-div">
      <!-- Hacer el css a mano del botón -->
      <button class="btn" type="button" @click="presionar">🔔</button>
    </div>

    <transition name="fade">
      <div class="dialogo" v-if="mostrar">
        <h6>Notificaciones</h6>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Notificacion',
  data() {
    return {
      mostrar: false,
    }
  },
  methods: {
    presionar() {
      this.mostrar = !this.mostrar
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

.dialogo {
  width: 400px;
  height: 200px;
  background-color: #80e3b3;
  position: fixed;
  top: 72vh;
  right: 6vw;
  border-radius: 15px 15px 1px 15px;
  padding: 25px;
  transition: 0.3s;
}

fade-enter-active,
.fade-leave-active {
  transition: 0.3s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transition: 0.3s;
}

h6 {
  text-align: center;
}
</style>
