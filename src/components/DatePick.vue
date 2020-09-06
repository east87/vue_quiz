<template>
  <div>
    <b-form-datepicker
    placeholder="YYYY-MM-DD"
    v-model="value" 
    :min="min" :max="max" 
    :date-format-options="{ year: 'numeric', month:'short', day: '2-digit'}"
    locale="en"></b-form-datepicker>
  </div>
</template>

<script>
  export default {
    
    data() {
      const now = new Date()
      const today = new Date(now.getFullYear(), now.getMonth(), now.getDate())
      // 15th two months prior
      const minDate = new Date(today)
      minDate.setMonth(minDate.getMonth() - 1200)
      minDate.setDate(15)
      // 15th in two months
      const maxDate = new Date(today)
      maxDate.setMonth(maxDate.getMonth() - 180)
      maxDate.setDate(15)

      console.log(minDate)

      return {
        value: '',
        min: minDate,
        max: maxDate
      }
    }
  }
</script>