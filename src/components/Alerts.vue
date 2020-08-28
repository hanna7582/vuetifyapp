<template>
  <v-row>
    <v-col sm="auto" cols="12">  
      <v-btn
        color="blue"
        dark
        @click="alert = !alert"
      >
        Toggle
      </v-btn>
    </v-col>
    <v-col >
      <v-alert 
        :value="alert"
        color="pink"
        dark
        border="left"
        prominent
        type="warning"
        transition="scale-transition"
        width="100%"
      >
        alert message.
      </v-alert>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
       alert: true 
    }
  },
 // data:() => ({ alert: true } )
}
</script>

<style>
</style>