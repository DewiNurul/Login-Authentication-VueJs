<template>
    <div class="container-scroller">
    <div class="container-fluid page-body-wrapper full-page-wrapper">
      <div class="main-panel">
        <div class="content-wrapper d-flex align-items-center auth">
          <div class="row w-100">
            <div class="col-lg-4 mx-auto">
              <div class="auth-form-light text-left p-5">
                <h4>Selamat datang!</h4>
                <h6 class="font-weight-light">Registrasi dahulu ya :)</h6>
                <form v-on:submit.prevent="Register" class="pt-3" method="post">
                  <div class="form-group">
                    <div class="input-group">
                      <input v-model="name" type="text" class="form-control form-control-lg" id="name" name="name" placeholder="Name" required>
                    </div>
                  </div>

                  <div class="form-group">
                    <div class="input-group">
                      <input v-model="email" type="email" class="form-control form-control-lg" id="email" name="email" placeholder="Email" required>
                    </div>
                  </div>

                  <div class="form-group">
                    <div class="input-group">
                      <input v-model="password" type="password" class="form-control form-control-lg" name="password" id="password" placeholder="New Password" required>                        
                    </div>
                  </div>

                  <div class="form-group">
                    <div class="input-group">
                      <input v-model="password_verify" type="password" class="form-control form-control-lg" name="password_verify" id="password_verify" placeholder="Retype Your New Password" required>                        
                    </div>
                  </div>

                  <div class="my-3">
                    <input type="submit" name="submit" class="btn btn-block btn-primary btn-lg font-weight-medium auth-form-btn" value="REGISTER">
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
</template>

<script>
export default {
    data() {
      return {
        name: '',
        email: '',
        password: '',
        password_verify: '',
      }
    },
    methods: {
        Register: function(){
            let name = this.name
            let email = this.email //let itu variabel baru
            let password = this.password
            let password_verify = this.password_verify
            this.$store.dispatch('register', { 
              name,
              email,
              password,
              password_verify,
              })
            .then(() => this.$router.push('/login'))
            .catch(err => console.log(err));


        }
    }
}
</script>