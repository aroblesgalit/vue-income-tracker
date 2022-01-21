<template>
  <div class="income-list">
    <IncomeItem v-for="item in income" :key="item.id" :income="item" />
  </div>
</template>

<script>
import IncomeItem from './IncomeItem'

export default {
  name: 'IncomeList',
  components: {
    IncomeItem
  },
  props: {
    income: Object
  }
}
</script>

<style scoped>
.income-list {
  margin-top: 30px;
  padding: 15px;
}
</style>
