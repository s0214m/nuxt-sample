<template>
  <div>
    <div>test2</div>
    <v-text-field ref="number" v-model="number" />
    <div>数値:{{ number }}</div>
    <div :class="$style.container" v-for="user in users" :key="user.id">
      <div>名前：{{ user.name }}</div>
      <div>メール：{{ user.email }}</div>
      <div>電話番号：{{ user.phone }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      number: 0,
      users: [],
    }
  },
  async created() {
    try {
      const response = await this.$axios.get(
        'http://jsonplaceholder.typicode.com/users'
      )
      this.users = response.data
      console.log(response)
    } catch (err) {
      const res = err.response
      console.log(res)
    }
  },
  mounted() {
    console.log('mounted')
    this.$refs.number.focus()
  },
  updated() {
    console.log('updated')
    console.log(this.number)
  },
}
</script>

<style lang="scss" module>
.container {
  margin: 10px 0;
  padding: 8px;
  border: 5px solid #ccc;
  border-radius: 4px;
}
</style>
