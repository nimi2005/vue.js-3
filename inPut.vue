<template>
  <input type="text" :value="modelValue" @input="$emit('update:modelVlaue',$event.target.value)"/>
</template>

<script>
export default {
 name: 'inPut',
 props:{
   modelValue: String
 }
}
</script>

<style scoped>
input[type = "text"],
textarea,
select{
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>