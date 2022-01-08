<template>
  <div class="home">
    <h1>SoufZone</h1>
    <SoufZone @drop.prevent = "drop" @change="selectedFile" />
    <div v-if="soufzoneFile">
    <h3 class="file-info">File Name : {{soufzoneFile.name}}</h3>
    <h3  class="file-info">File Size : {{soufzoneFile.size / 1000}} KB</h3>
    <h3 v-if="soufzoneFile.type" class="file-info">File Type : {{soufzoneFile.type}}</h3>
    <h3 class="file-info">File Last Modified : {{soufzoneFile.lastModifiedDate}}</h3>

    </div>

    
  </div>
</template>

<script>

import SoufZone from '@/components/SoufZone.vue';
import {ref} from "vue";
export default {
  name: 'Home',
  components: {
    SoufZone
  },
  setup(){
    let soufzoneFile = ref("");
    const drop = (e)=>{
      soufzoneFile.value = e.dataTransfer.files[0];
    }
    const selectedFile = ()=>{
      soufzoneFile.value = document.querySelector('#soufzoneFile').files[0];
    }
    return {
      soufzoneFile,drop,selectedFile
    };
  }
}
</script>
<style lang="scss" scoped>
.home{
  width:100vw;
  height:100vh;
  display:flex;
  justify-content: center;
  align-items: center;
  flex-direction:column;
  h1{
    font-size:40px;
    margin-bottom:32px;
    color:#1ab7ea;
  }
  .file-info{
    margin-top:32px;
  }
  h3{
    color:#162221;
    font-size:1rem;
    text-align:center;
  }
}

</style>