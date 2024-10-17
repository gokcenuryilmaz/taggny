<template>
    <div class="tag-container">
        <TagGny 
            v-for="(tag,index) in tags"
            :tag="tag"
            :index="index"
            :key="index"
            :tagColor="color"
            @removeOneTagEvent="removeOneTag(index)"
        ></TagGny>
        <input 
            type="text" 
            @keydown.enter="addTag"
            @keydown.backspace="removeTag">
        <div class="error" v-if="error">Bu etiket daha önceden eklenmiş</div>
    </div>
</template>
<script>
import TagGny from "./TagGny.vue"
    export default{
        components : {
            TagGny
        },
        data(){
            return{
                tags : [],
                error : false,
              
            }
        },
        methods: {
          addTag(event){
            let text = event.target
            let matchedTag = false
            
            if(text.value.length > 0){
              this.tags.forEach(tag =>{
              if(tag.toLowerCase() === text.value.toLowerCase()){
                matchedTag = true
              }
            })

            if(!matchedTag){
              this.tags.push(text.value)
              text.value = ""; // Input alanını temizle
            }else{
              this.error = true;
         
            setTimeout(()=>{
              this.error =false
              text.value = ""; // Input alanını temizle
            }, 2000)

        }
      }
            },
          removeTag(e){
              if(e.target.value.length <= 0){
              this.tags.splice(this.tags.length-1,1);
            }
          },
          removeOneTag(index){
                this.tags.splice(index,1)
          }
        },
        props: {
          value : {
            required : false
          },
          color : {
            type : String,
            required : false,
            default : "primary"
          }
        },
        created(){
          if(this.value){
            if(this.value.length > 0){
              this.tags = this.value.split(",") //geelecek veriyi virgülden patlat ve tags'e yaz
            }
          }
        },
        watch : {
          //verimin güncellenip güncellenmediğini izler
          tags(){
            this.$emit("input",this.tags.join(","))// arrayi yapıştırır ve yukariya haber ver
          }//tagsim değiştiği zaman çalışan value ile birlikte birleştir.
        }
    }
</script>
<style scoped>
    input{
        outline: none;
        height: 30px;
        width: 100px;
        margin-right: 10px;
    }
    .error{
        font-size: 12px;
        color: red;
        margin-top: 5px;
    }
</style>