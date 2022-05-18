<script lang="ts">
export default {
  props: {
    customer: {
      id: String,
      first_name: String,
      last_name: String,
      address: String,
      city: String,
      zipcode: String,
      email: String
    }
  }
}
</script>

<template>
  <div>
    <div>Id: {{ this.$props.customer.id }}</div>
    <div>First name: {{ this.$props.customer.first_name }}</div>
    <div>Last name: {{ this.$props.customer.last_name }}</div>
    <div>Address: {{ this.$props.customer.address }}</div>
    <div>City: {{ this.$props.customer.city }}</div>
    <div>Zipcode: {{ this.$props.customer.zipcode }}</div>
    <div>E-mail: {{ this.$props.customer.email }}</div>
  </div>
</template>