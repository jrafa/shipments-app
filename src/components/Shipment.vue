<script lang="ts">
import "bootstrap/dist/css/bootstrap.min.css";
import moment from "moment";

import Customer from "@/components/Customer.vue";

export default {
  data() {
    return {shipments: []}
  },
  mounted() {
    fetch('http://localhost:8000/api/v1/shipments')
        .then(res => res.json())
        .then(data => this.shipments = data)
        .catch(err => console.log(err.message))
  },
  components: {
    Customer
  },
  methods: {
    formatDateTime: function (date) {
      return moment(date).format('MMMM Do YYYY, h:mm:ss a');
    },
    formatHeader: function (text) {
      return text.replace("_", " ").toUpperCase()
    }
  }
}

</script>

<template>
  <div class="shipments">
    <h3>Shipments</h3>
    <div v-if="!shipments.length">No item in shipments</div>
    <div>
      <table id="tableComponent" class="table table-bordered table-striped">
        <thead>
        <tr>
          <th v-for="(value, name) in shipments[0]" :key="name">{{ formatHeader(name) }}</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="shipment in shipments" :key="shipment">
          <td>{{ shipment.id }}</td>
          <td>{{ formatDateTime(shipment.post_date) }}</td>
          <td>{{ formatDateTime(shipment.received_date) }}</td>
          <td>
            <div v-for="sender in shipment.sender" :key="sender">
              <Customer :customer="sender"/>
            </div>
          </td>
          <td>
            <div v-for="recipient in shipment.recipient" :key="recipient">
              <Customer :customer="recipient"/>
            </div>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
