<template>

  <div>
  <Header/>
  <section class="">
    <div class="container h-100">
      <div class="row justify-content-md-center">
        <div class="col-md-8 bg-white pt-5">
          <StepFormValidation/>
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
import StepFormValidation from '@/components/StepFormValidation.vue'
import FooterBar from '@/components/FooterBar.vue'
export default {
  components: {
    Header, StepFormValidation,FooterBar
  }
}
</script>
