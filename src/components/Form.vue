<template>
  <form @submit.prevent="FormHandler">
    <input type="text" placeholder="Description..." v-model="desc" />
    <input type="number" placeholder="Value..." v-model="value" />
    <input type="date" placeholder="Date..." v-model="date" />
    <input type="submit" value="SUBMIT" />
  </form>
</template>

<script>
export default {
  name: 'Form',
  props: {
    state: Object
  },
  data () {
    return {
      desc: null,
      value: null,
      date: null
    }
  },
  methods: {
    FormHandler () {
      if (!this.desc || !this.date) {
        alert('Please fill in empty field.')
        return
      }

      let d = this.date.split('-')
      let newD = new Date(d[0], d[1], d[2])

      const newIncome = {
        id: Date.now(),
        desc: this.desc,
        value: this.value,
        date: newD.getTime()
      }

      this.$emit('add-income', newIncome)

      this.desc = null
      this.value = null
      this.date = null
    }
  }
  //   emits: [desc, value, date]
}
</script>

<style scoped>
form {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}
form input {
  color: #888;
  border: none;
  outline: none;
  font-size: 20px;
}
form input::placeholder {
  color: #aaa;
}
form input:not([type='submit']) {
  display: block;
  background: #fff;
  border: none;
  outline: none;
  padding: 5px 15px;
}
form input[type='submit'] {
  display: block;
  background: none;
  border: none;
  outline: none;
  color: #fff;
  font-weight: 500;
  text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
  padding: 5px 15px;
  background-color: #ffce00;
  cursor: pointer;
}
form input:first-of-type {
  border-radius: 8px 0px 0px 8px;
}
form input:last-of-type {
  border-radius: 0px 8px 8px 0px;
}
</style>
