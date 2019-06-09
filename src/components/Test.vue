<template>
  <div class="test">
    <h1>{{ msg }}</h1>
    <h2>Banner bugfix</h2>
    <input v-model="keyword">
    <ul>
      <li v-for='banner in filteredBanners' :key="banner.id">
          <banner
            v-bind:headMsg="banner.hmsg"
            v-bind:bodyMsg="banner.bmsg"
            v-bind:footMsg="banner.fmsg"
          ></banner>
      </li>
    </ul>
  </div>
</template>

<script>
import Banner from './Banner'
export default {
  name: 'Test',
  components: {
    Banner
  },
  data () {
    return {
      msg: 'This is test page',
      banners: [],
      keyword: ''
    }
  },
  mounted: function () {
    let arr = []
    for (let i = 1; i < 21; i++) {
      let val = {}
      if (i % 2 === 0) {
        val = {id: i, hmsg: 'banner' + i, bmsg: 'body test ' + i, fmsg: 'fmsg' + i}
      } else {
        val = {id: i, hmsg: 'banner' + i, bmsg: 'body practice ' + i, fmsg: 'fmsg' + i}
      }
      arr.push(val)
    }
    this.banners = arr
  },
  computed: {
    filteredBanners: function () {
      return this.banners.filter(banner => { return banner.bmsg.includes(this.keyword) }, this)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
