<template>
  <div>
    <!-- v-ifとその仲間達 -->
    <div v-if="score >= 80">よく出来ました！</div>
    <div v-else-if="score >= 30">もっといけるで！</div>
    <div v-else>切り替えてこ！！</div>

    <!-- <a :href="googleLink">Googleへのリンク</a> -->
    <img :src="imageUrl()" width="100px" />

    <!-- <v-btn @click="showMessage('クリック')">クリック</v-btn>
    <v-btn @dblclick="showMessage('ダブルクリック')">ダブルクリック</v-btn>
    <v-btn @mouseenter="showMessage('マウスエンター')">マウスエンター</v-btn> -->
    <!-- v-show -->
    <!-- <div v-show="isShown">見えるかな？</div>
    <v-btn @click="toggleShown">表示/非表示</v-btn> -->

    <!-- v-model -->
    <v-text-field v-model="score" />
    <input type="text" style="width: 100%" />

    <div v-for="fruit in fruits" :key="fruit.name">{{ fruit.name }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShown: true,
      score: 0,
      googleLink: 'https:/google.com',
      fruits: [
        { name: 'apple' },
        { name: 'orange' },
        { name: 'peach' },
        { name: 'banana' },
      ],
    }
  },
  methods: {
    toggleShown() {
      this.isShown = !this.isShown
    },
    imageUrl() {
      if (this.score >= 80) {
        return 'https://2.bp.blogspot.com/-zDsrPiqkR_0/U0pTNj7lpoI/AAAAAAAAfGA/2Z1onz10tAw/s800/grade2_yokudekimashita.png'
      } else if (this.score >= 30) {
        return 'https://2.bp.blogspot.com/-wJDmO2MIKkg/U0pTOEZT-JI/AAAAAAAAfGc/p9uwt9Msq9A/s800/grade3_ganbarimashita.png'
      } else {
        return 'https://2.bp.blogspot.com/-Bc8NTQ2PqY8/U0pTOuIDWQI/AAAAAAAAfGY/1RU2LKdozKs/s800/grade5_ganbarimasyou.png'
      }
    },
    showMessage(message) {
      alert(message)
    },
  },
}
</script>
