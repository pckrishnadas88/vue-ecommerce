<template>
    <div class="login container">
        <form class="col-md-6 login-form">
            <FormInput :v-bind:value="email" name="Email" type="email" label="Email" />
            <FormInput :value="password" name="password" type="password" label="Password" />
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>        
    </div>
</template>
<script>
// @ is an alias to /src
import FormInput from '@/components/forms/FormInput.vue';

export default {
  name: "Login",
  data () {
    return {
      email: null,
      password: null
    }
  },
  mounted () {
    
  },
  components: {
    FormInput,
  },
};
</script>
<style scoped>
.login-form {
    margin: auto;
}
</style>