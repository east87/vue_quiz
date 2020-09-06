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
					</div>
				</div>
          <div class="d-flex justify-content-center form_container">
            <form>
              <div class="input-group mb-3">
                <div class="input-group-append">
                  <span class="input-group-text">
                    <i class="fas fa-user"></i>
                  </span>
                </div>
                <input
                  type="text"
                  name
                  class="form-control input_user"
                  value
                  placeholder="username"
                />
              </div>
              <div class="input-group mb-2">
                <div class="input-group-append">
                  <span class="input-group-text">
                    <i class="fas fa-key"></i>
                  </span>
                </div>
                <input
                  type="password"
                  name
                  class="form-control input_pass"
                  value
                  placeholder="password"
                />
              </div>
              <div class="form-group">
                <div class="custom-control custom-checkbox">
                  <input type="checkbox" class="custom-control-input" id="customControlInline" />
                  <label class="custom-control-label" for="customControlInline">Remember me</label>
                </div>
              </div>
              <div class="d-flex justify-content-center mt-3 login_container">
                <button type="button" name="button" class="btn login_btn">Login</button>
              </div>
               <div class="d-flex justify-content-center links">
						<a href="#">Forgot your password?</a>
					</div>
            </form>
            
          </div>
          <div class="sign-info">
               <div class="d-flex justify-content-center links">
						Don't have an account? <a href="#" class="ml-2">Sign Up</a>
					</div>
					
               <ul class="iq-social-media">
                     <li><a href="#"><i class="ri-facebook-box-line"></i></a></li>
                     <li><a href="#"><i class="ri-twitter-line"></i></a></li>
                     <li><a href="#"><i class="ri-instagram-line"></i></a></li>
               </ul>
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
  name: 'Signin',
  components: {
    Header,FooterBar
  }
}
</script>

<style scoped>
.sign-in-page{
max-height: 92vh;
}
	.user_card {
		max-height: 500px;
			width: 350px;
			margin-top: auto;
			margin-bottom: auto;
			background: #89b5f7;
			position: relative;
			display: flex;
			justify-content: center;
			flex-direction: column;
			padding: 10px;
			box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
			-webkit-box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
			-moz-box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
			border-radius: 5px;

		}
		.brand_logo_container {
			position: absolute;
    /* height: 69px; */
    /* width: 170px; */
    top: -3px;
    /* border-radius: 50%; */
    /* background: #60a3bc; */
    padding: 10px;
		}
	
	
		
		.login_btn {
			width: 100%;
			background: #c0392b !important;
			color: white !important;
		}
		.login_btn:focus {
			box-shadow: none !important;
			outline: 0px !important;
		}
		.login_container {
			padding: 0 2rem;
		}
		.input-group-text {
			background: #c0392b !important;
			color: white !important;
			border: 0 !important;
			border-radius: 0.25rem 0 0 0.25rem !important;
		}
		.input_user,
		.input_pass:focus {
			box-shadow: none !important;
			outline: 0px !important;
		}
		.custom-checkbox .custom-control-input:checked~.custom-control-label::before {
			background-color: #c0392b !important;
		}
</style>