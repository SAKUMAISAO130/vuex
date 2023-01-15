<template>
  <div class="about">
    <div><input type="text" v-model="title"></div>
    <div><textarea name="" id="" cols="30" rows="10" v-model="content"></textarea></div>
    <div class="center">
      <button @click="save">保存</button>
      <button @click="remove" v-if="memo.id">削除</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'MemoForm',
  props: [
    'memo'
  ],
  data(){
    return{
      title:this.memo.title,
      content:this.memo.content
    }
  },
  methods: {
    save(){
      let memo = {
        title: this.title,
        content: this.content
      }

      if(this.memo.id) {
        memo.id = this.memo.id
      }

      this.$store.commit('save', memo)
      this.$router.push('/')
    },
    remove(){
      this.$store.commit('delete', this.memo.id)
      this.$router.push('/')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
