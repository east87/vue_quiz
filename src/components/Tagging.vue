<template>
  <div>
    <label for="tags-pills">Enter tags</label>
    <b-form-tags
      input-id="tags-pills"
      v-model="value"
      tag-variant="primary"
      tag-pills
      size="md"
      separator=" "
      placeholder="Enter new tags separated by space"
      class="mb-2"
    ></b-form-tags>
    <p>Value: {{ value }}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        value: ['apple', 'orange', 'grape']
      }
    }
  }
</script>