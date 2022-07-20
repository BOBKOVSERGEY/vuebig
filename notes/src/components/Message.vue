<template>
  <div class="message">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String, // String? Number Array Object Bool
      //required: true
      default: 'default message'
    }
  }
}
</script>
