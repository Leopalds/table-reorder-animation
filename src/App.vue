<template>
  <table>
    <thead>
      <tr class="header">
        <th class="header-row" v-for="header in data.headers" :key="header">{{ header }}</th>
      </tr>
    </thead>
    <transition-group tag="tbody" name="table-row" class="table-body">
      <tr class="body-row" v-for="row in Object.values(data.rows)" :key="row.id">
        <td class="body-cell" v-for="cell in Object.values(row)" :key="cell">{{ cell }}</td>
      </tr>
    </transition-group>
  </table>

  <div class="reorder-button" @click="reorder">Reorder</div>
</template>

<script setup>
import { ref } from 'vue'

const data = ref({
  headers: ['id', 'name', 'amount', 'price'],
  rows: [
    { id: 1, name: 'Apple', amount: 10, price: 1.5 },
    { id: 2, name: 'Banana', amount: 20, price: 2.5 },
    { id: 3, name: 'Cherry', amount: 30, price: 3.5 },
    { id: 4, name: 'Date', amount: 40, price: 4.5 },
    { id: 5, name: 'Elderberry', amount: 50, price: 5.5 },
    { id: 6, name: 'Fig', amount: 60, price: 6.5 },
    { id: 7, name: 'Grape', amount: 70, price: 7.5 },
    { id: 8, name: 'Honeydew', amount: 80, price: 8.5 },
    { id: 9, name: 'Kiwi', amount: 90, price: 9.5 },
    { id: 10, name: 'Lemon', amount: 100, price: 10.5 }
  ]
})

const reorder = () => {
  data.value.rows = data.value.rows.sort(() => Math.random() - 0.5)
}
</script>

<style scoped>
.reorder-button {
  cursor: pointer;
  padding: 10px;
  background-color: #007bff;
  color: white;
  text-align: center;
  margin-top: 10px;
  margin-left: 10px;
  height: fit-content;
  border-radius: 12px;
}

table, th, td {
  border-collapse: collapse;
  padding: 10px;
  text-align: left;
  border: 1px solid rgb(160 160 160) !important;
}

.table-row-move {
  transition: transform 0.5s ease;
}
</style>
