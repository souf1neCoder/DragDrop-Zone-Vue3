<template>
  <div
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
    :class="{ 'active-dropzone': active }"
    class="soufzone"
  >
    <h4>Drag or Drop File</h4>
    <h4>OR</h4>
    <label for="soufzoneFile">Select File</label>
    <input type="file"  id="soufzoneFile" />
  </div>
</template>

<script>
import {ref} from "vue";

export default {
  name: "SoufZone",
  setup(){
      const active = ref(false);
      const toggleActive = () =>{
          active.value = !active.value;
      };
      return {active,toggleActive};
  }
};
</script>

<style scoped lang="scss">
.soufzone {
  width: 400px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 16px;
  border: 2px dashed #1ab7ea;
  background: #fff;
  transition: 0.3s ease all;
  label {
    background: #1ab7ea;
    padding: 8px 12px;
    color: #fff;
    transition: 0.3s ease all;
    cursor:pointer;
  }
  input {
    display: none;
  }
  h4{
      color:#899cab;
  }
}
.active-dropzone{
    color:#fff;
    border-color:#fff;
    background-color: #1ab7ea;
    label{
        background-color: #fff;
        color:#1ab7ea;
    }
}
</style>