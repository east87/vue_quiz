<template>
  <form-wizard @onComplete="onComplete">
    <p>Lets create your mindchaster account</p>
    <tab-content title="About You" :selected="true">
      <div class="form-row">

        <div class="col form-group">
          <b-form-input
            type="text"
            class="form-control"
            :class="hasError('firstName') ? 'is-invalid' : ''"
            placeholder="Enter your first name"
            v-model="formData.firstName"
          ></b-form-input>
          <div v-if="hasError('firstName')" class="invalid-feedback">
            <div
              class="error"
              v-if="!$v.formData.firstName.required"
            >Please provide a valid first name.</div>
          </div>
        </div>

        <div class="col form-group">
          <b-form-input
            type="text"
            class="form-control"
            :class="hasError('lastName') ? 'is-invalid' : ''"
            placeholder="Enter your last name"
            v-model="formData.lastName"
          >
          </b-form-input>
          <div v-if="hasError('lastName')" class="invalid-feedback">
            <div
              class="error"
              v-if="!$v.formData.lastName.required"
            >Please provide a valid last name.</div>
          </div>
        </div>
      </div>

      <b-input-group class="form-group">
        <b-input-group prepend="@" class="mb-2 mr-sm-2 mb-sm-0">
          <b-input
            type="text"
            class="form-control"
            :class="hasError('username') ? 'is-invalid' : ''"
            placeholder="username"
            v-model="formData.username"
          ></b-input>
          <div v-if="hasError('username')" class="invalid-feedback">
            <div class="error" v-if="!$v.formData.username.required">Username field is required</div>
          </div>
        </b-input-group>
        <label>Use 8 or more characters with mix off letter, number & symbol</label>
      </b-input-group>
      <b-input-group class="form-row">
        <b-input-group class="col form-group">
          <b-input-group-prepend is-text>
            <b-icon icon="lock-fill"></b-icon>
          </b-input-group-prepend>
          <b-form-input
            type="password"
            class="form-control"
            :class="hasError('lastName') ? 'is-invalid' : ''"
            placeholder="password"
            v-model="formData.password"
          ></b-form-input>
          <div v-if="hasError('password')" class="invalid-feedback">
            <div
              class="error"
              v-if="!$v.formData.password.required"
            >Please provide a valid password.</div>
            <div class="error" v-if="!$v.formData.password.minLength">Min 6 characters</div>
          </div>
        </b-input-group>

        <b-input-group class="col form-group">
          <b-form-input
            type="password"
            class="form-control"
            :class="hasError('conpassword') ? 'is-invalid' : ''"
            placeholder="Confirm password"
            v-model="formData.conpassword"
          ></b-form-input>
          <div v-if="hasError('conpassword')" class="invalid-feedback">
            <div
              class="error"
              v-if="!$v.formData.conpassword.required"
            >Please provide a valid password confirmation.</div>
            <div
              class="error"
              v-if="!$v.formData.conpassword.sameAsPassword"
            >Please provide a valid password confirmation.</div>
          </div>
        </b-input-group>
      </b-input-group>
      <DatePick />
     

    </tab-content>

    
    <tab-content title="Additional Info">
      <b-input-group class="form-group">
        <b-input-group-prepend is-text>
          <b-icon icon="envelope-fill"></b-icon>
        </b-input-group-prepend>
        <b-form-input
          type="email"
          class="form-control"
          :class="hasError('email') ? 'is-invalid' : ''"
          placeholder="email"
          v-model="formData.email"
        ></b-form-input>
        <div v-if="hasError('email')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.email.required">Email field is required</div>
          <div class="error" v-if="!$v.formData.email.email">Should be in email format</div>
        </div>
      </b-input-group>


  <b-input-group class="form-group">
        <b-input-group-prepend is-text>
          <b-icon icon="phone-fill"></b-icon>
        </b-input-group-prepend>
        <b-form-input
          type="test"
          class="form-control"
          :class="hasError('phone') ? 'is-invalid' : ''"
          placeholder="phone"
          v-model="formData.phone"
        ></b-form-input>
        <div v-if="hasError('email')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.phone.required">Email field is required</div>
        </div>
      </b-input-group>

    

    

   <label for="tags-pills">Enter tags</label>
    <b-form-tags
      input-id="tags-pills"
      v-model="formData.taging"
      tag-variant="primary"
      tag-pills
      size="md"
      separator=" "
      placeholder="Enter new tags separated by space"
      class="mb-2"
    ></b-form-tags>
    <p>Value: {{ formData.taging }}</p>

    <div class="form-group form-check">
        <input
          type="checkbox"
          :class="hasError('terms') ? 'is-invalid' : ''"
          class="form-check-input"
          v-model="formData.terms"
        />
        <label class="form-check-label">I accpet terms & conditions</label>
        <div v-if="hasError('terms')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.terms.required">Please select terms and conditions.</div>
        </div>
      </div>


    </tab-content>


    
  </form-wizard>
</template>

<script>
import { FormWizard, TabContent, ValidationHelper } from "vue-step-wizard";
import "vue-step-wizard/dist/vue-step-wizard.css";
import { required } from "vuelidate/lib/validators";
import { email } from "vuelidate/lib/validators";
//import { numeric } from "vuelidate/lib/validators";
import { sameAs } from "vuelidate/lib/validators";
import { minLength } from "vuelidate/lib/validators";
import DatePick from "../components/DatePick.vue";
export default {
  name: "StepFormValidation",
  components: {
    FormWizard,
    TabContent,
    DatePick
  },
  mixins: [ValidationHelper],
  data() {
    return {
      formData: {
        firstName: "",
        lastName: "",
        username: "",
        password: "",
        conpassword: "",
        email: null,
        phone: '',
        taging: ['apple', 'orange', 'grape'],
        terms: false,
      },
      validationRules: [
        {
          firstName: { required },
          lastName: { required },
          username: { required },
          password: { required, minLength: minLength(6) },
          conpassword: {
            required, minLength: minLength(6), sameAsPassword: sameAs("password")
          }
        },
        { email: { required, email }, phone: { required },  terms: { required } }
        
      ]
    };
  },
  methods: {
    onComplete() {
      alert("Submitting Form ! Rock On");
    },
  },
};
</script>

<style scoped>
.card {
  margin-top: 5%;
}
</style>>