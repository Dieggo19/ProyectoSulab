<template>
  <section class="vh-100 gradient-custom">
    <div class="container py-5 h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-12 col-md-8 col-lg-6 col-xl-5">
          <div class="card bg-dark text-white" style="border-radius: 1rem">
            <div class="card-body p-5 text-center">
              <img src="../static/icono-sulab.png" />
              <div class="mb-md-5 mt-md-4 pb-5">
                <h2 class="fw-bold mb-2 text-uppercase">Sulab Inventario</h2>
                <p class="text-white-50 mb-5">
                  Por favor, ingrese su nombre de usuario y contraseña
                </p>

                <div class="form-outline form-white mb-4">
                  <input
                    type="email"
                    id="typeEmailX"
                    class="form-control form-control-lg"
                    v-model="email"
                  />
                  <label class="form-label" for="typeEmailX"
                    >Nombre de usuario</label
                  >
                </div>

                <div class="form-outline form-white mb-4">
                  <input
                    type="password"
                    id="typePasswordX"
                    class="form-control form-control-lg"
                    v-model="password"
                  />
                  <label class="form-label" for="typePasswordX"
                    >Contraseña</label
                  >
                </div>

                <button
                  class="btn btn-outline-light btn-lg px-5"
                  type="submit"
                  @click="login"
                >
                  Entrar
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    login() {
      this.$router.push('/productos')
    },
  },
}
</script>

<style scoped>
.gradient-custom {
  /* fallback for old browsers */
  background: #6a11cb;

  /* Chrome 10-25, Safari 5.1-6 */
  background: -webkit-linear-gradient(to right, #5ab037, rgba(37, 117, 252, 1));

  /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  background: linear-gradient(to right, #5ab037, rgb(145, 181, 243));
}

img {
  width: 200px;
  height: 200px;
  background-color: white;
  border-radius: 50%;
}
</style>
