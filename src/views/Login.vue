<template>
    <div class="container-scroller">
    <div class="container-fluid page-body-wrapper full-page-wrapper">
      <div class="main-panel">
        <div class="content-wrapper d-flex align-items-center auth">
          <div class="row w-100">
            <div class="col-lg-4 mx-auto">
              <div class="auth-form-light text-left p-5">
                <h4>Selamat datang!</h4>
                <h6 class="font-weight-light">Silahkan login ya :)</h6>
                <form v-on:submit.prevent="Login" class="pt-3" method="post" action="#">
                <div class="form-group">
                  <div class="input-group">
                    <input v-model="email" type="email" class="form-control form-control-lg" id="email" name="email" placeholder="Email" required>
                  </div>
                </div>
                <div class="form-group">
                  <div class="input-group">
                    <input v-model="password" type="password" class="form-control form-control-lg" name="password" id="password" placeholder="Password" required>                        
                  </div>
                </div>
                <div class="my-3">
                  <input type="submit" name="submit" class="btn btn-block btn-primary btn-lg font-weight-medium auth-form-btn" value="MASUK">
                </div>
              </form>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- content-wrapper ends -->
    </div>
    <!-- page-body-wrapper ends -->
  </div>
  <!-- container-scroller -->
</template>

<script>
export default {
    data() {
      return {
        email: '',
        password: ''
      }
    },
    methods: {
        Login: function(){
            let email = this.email //let itu variabel baru
            let password = this.password
            this.$store.dispatch('login', { email, password })
            .then(() => this.$router.push('/home'))
            .catch(err => console.log(err))
        }
    }
}
</script>