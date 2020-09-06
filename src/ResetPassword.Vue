<template>
  <div>
  <Header/>
 <section class="sign-in-page">
    <div class="container h-100">
      <div class="d-flex justify-content-center h-100">
        <div class="user_card">
          <div class="d-flex justify-content-center">
					<div class="title-signin">
						<h1>Signin</h1>
                        <p>Enter your email address and we'll send you an email with instructions to reset your password.</p>
					</div>
				</div>
          <div class="d-flex justify-content-center form_container">
            <form class="mt-4">

                                <div class="form-group">
                                    <label for="exampleInputEmail1">Email address</label>
                                    <input type="email" class="form-control mb-0" id="exampleInputEmail1" placeholder="Enter email">
                                </div>

                                <div class="d-inline-block w-100">

                                    <button type="submit" class="btn btn-primary float-right">Reset Password</button>
                                </div>

                            </form>
            
          </div>
          
        </div>
      </div>
    </div>
  </section>
  <section>
  <FooterBar/>
  </section>
  </div>

  
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import FooterBar from '@/components/FooterBar.vue'
export default {
  name: 'ResetPassword',
  components: {
    Header,FooterBar
  }
}
</script>

<style scoped>
.sign-in-page{
max-height: 92vh;
}
	
</style>