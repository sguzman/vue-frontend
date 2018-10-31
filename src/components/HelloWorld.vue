<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ limit }}</h2>
    <input v-model="msg" placeholder="Enter text" />
    <label>
      <input type="range" v-model="limit" min="1" max="100" value="10" step="1"  />
    </label>
    <button @click="get"></button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'UC-lHJZR3Gqxm24_Vd_AJ5Yw',
      limit: 10
    }
  },
  methods: {
    get () {
      const xhttp = new XMLHttpRequest()
      xhttp.onreadystatechange = function () {
        if (this.readyState === 4 && this.status === 200) {
          console.log(JSON.parse(this.responseText))
        }
      }
      xhttp.open('GET', `http://192.168.1.63:30003/${this.msg}/${this.limit}`, true)
      xhttp.send()
    }
  }
}
</script>
