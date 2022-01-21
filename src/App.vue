<template>
  <Header :totalIncome="totalIncome" />
  <Form @add-income="addIncome" />
  <IncomeList :income="sortedIncome" />
</template>

<script>
import Header from './components/Header'
import Form from './components/Form'
import IncomeList from './components/IncomeList'

export default {
  name: 'App',
  components: {
    Header,
    Form,
    IncomeList
  },
  data () {
    return {
      income: []
    }
  },
  methods: {
    addIncome (income) {
      this.income = [...this.income, income]
    }
  },
  computed: {
    totalIncome () {
      let temp = 0
      if (this.income.length > 0) {
        for (let i = 0; i < this.income.length; i++) {
          temp += this.income[i].value
        }
      }
      return temp
    },
    sortedIncome () {
      return [...this.income].sort(function (a, b) {
        return b.date - a.date
      })
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

body {
  background: #eee;
}
</style>
