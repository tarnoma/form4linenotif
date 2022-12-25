<template>
  <q-page padding>
    <q-input
        v-model="textareaModel"
        filled
        type="textarea"
        color="red-12"
        label="Textarea with shadow text"

       
      />

      <q-btn round color="secondary" icon="send" @click="Send"/>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import {api} from 'boot/axios'
export default defineComponent({
  name: 'IndexPage',
  data(){
  return{textareaModel : ""
  }
  },
  methods:{
    Send(){
      // console.log(this.textareaModel)
      // console.log(api)
      // const header = {
      //   "Content-Type" : "application/x-www-form-urlencoded",
      //   "Authorization" : "Bearer GqOmUoAyxaJX626osTbLCMIwBxc9UjIIDWjRCwYXBb0"
        
      // }
      const data ={
          "message" : this.textareaModel
      }
      api.post("/msg", data).then((respond)=>{if (respond.status == 200){console.log("Yay Complete")}}).catch((error)=>{console.log(error)})
      this.textareaModel = ""

    }
  }
})
</script>
