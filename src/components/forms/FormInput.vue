<template>
    <div class="form-group">
        <label for="exampleInputEmail1">{{ label }}</label>
        <input :type="type" :value="value" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
    </div>
</template>
<script>
export default {
  name: "FormInput",
  props: {
    label: String,
    name: String,
    type: String,
    value: String,
  },
};
</script>