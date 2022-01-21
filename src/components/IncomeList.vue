<template>
  <div class="income-list">
    <IncomeItem />
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
    state: Object
  }
}
</script>

<style scoped>
.income-list {
  margin-top: 30px;
  padding: 15px;
}
</style>
