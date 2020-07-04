<template>
  <div class="flex h-screen w-full bg-gray-700 ">
    <div class="m-auto w-full px-5 md:w-1/3">
    <form>
      <inputElement 
        :labelName="'EMAIL'"
        :labelId="'email'"
        :inputType="'email'"
        :model="email"
        @input="email = $event"
        :disabled="false"
        />
        <inputElement 
        :labelName="'PASSWORD'"
        :labelId="'password'"
        :inputType="'password'"
        :model="password"
        @input="password = $event"
        :disabled="false"
        />
        <button type="button"> SIGN IN </button>
    </form>
    </div>
  </div>
</template>

<script>
import nuxtLogo from '~/components/items/Logo.vue';
import InputElement from "~/components/items/Input.vue";
export default {
  components:{
    nuxtLogo,
    InputElement
  },
  data: function(){    //variables to store input
    return{
      email:"",
      password:""
    }
  }
}
</script>
<style scoped>

</style>


