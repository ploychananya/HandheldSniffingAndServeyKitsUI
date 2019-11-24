<template>
  <div id="info">
    <div id="result" style="color: SlateBlue; font-size: 200%; font-family: Monaco, monospace; margin: 20px">{{info}}</div>
  </div>

</template>

<script>
  export default {
    name: 'LoraInfos',

    data() {
      return {
        products: []
      }
    },

    mounted() {
        // axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*';
        axios
            .get("http://192.168.4.1/lora",{headers:{}})
            .then(response => {
            this.products = response.data;
            });
    }
  }
</script>