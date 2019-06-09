<template>
  <div class="banner">
    <div class="banner-header">
      <h1>{{ headMsg }}</h1>
    </div>
    <div class="banner-body">
      <iframe ref="iframe" style="height: 410px;"></iframe>
    </div>
    <div class="banner-footer">
      <h3>{{ footMsg }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Banner',
  data () {
    return {
      msg: 'This is test page'
    }
  },
  props: {
    headMsg: {
      type: String,
      default: 'Banner header'
    },
    bodyMsg: {
      type: String,
      default: 'Banner body'
    },
    footMsg: {
      type: String,
      default: 'This is banner test'
    }
  },
  mounted: function () {
    this.setIframe()
  },
  destroyed: function(){
    console.log(this.headMsg)
  },
  methods: {
    setIframe: function (strValue) {
      var preview = this.$refs.iframe
      var idoc = preview.contentDocument
      var html = '<html><head></head><body><h2>' + this.bodyMsg + '</h2><img src="https://www.evernote.com/l/AOKJJhop2sFA-LERyu2z-Ou6b4rsGYrLi00B/image.png" /></body></html>'

      idoc.open()
      idoc.write(html)
      idoc.close()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.banner {
  border: solid 1px black;
  background-color: lightyellow;
  margin: 5px;
}
.banner-header {
  background-color: lightpink;
}
.banner-body {
  background-color: lightblue;
}
.banner-footer {
  background-color: lightgreen;
}
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
