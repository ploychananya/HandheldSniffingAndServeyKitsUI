<template>
  <div class="home" style="background-color: hsl(0, 0%, 95%);padding-bottom:100%">
    <img alt="Iwing logo"  src="../assets/iwing.png" style="margin-top:50px;" />
    <!--<HelloWorld msg="Welcome to Your Vue.js App" />
    
    -->
    <h1 style="font-size: 24px;font-family:sans-serif;font-weight:bold;">Handheld LoRa Survey & Sniffing Kits</h1>
    <br>
    <div style="background-color: hsl(0, 0%, 90%);padding-top:10px;padding-bottom:10px;margin-left:50px;margin-right:50px;">
    <nav class="level" >
      <div class="level-item has-text-centered">
        <div>
          <p class="heading">Frequency (Hz)</p>
          <div class="select">
            <select>
              <option>433E6</option>
              <option>169E6</option>
              <option>434E6</option>
              <option>866E6</option>
              <option>868E6</option>
              <option>915E6</option>
            </select>
          </div>
        </div>
      
     
        <div style="margin-left:50px">
          <p class="heading">Bandwidth (Hz)</p>
          <div class="select">
            <select>
              <option>125E3</option>
              <option>250E3</option>
              <option>20.8E3</option>
              <option>7.8E3</option>
              <option>15.6E3</option>
              <option>31.25E3</option>
            </select>
          </div>
      
        </div>
      </div>
      </nav>

      <nav class="level">
      <div class="level-item has-text-centered">
        <div>
          <p class="heading">Spreading factor</p>
          <div class="select">
            <select>
              <option>7</option>
              <option>8</option>
              <option>9</option>
              <option>10</option>
              <option>11</option>
              <option>12</option>
            </select>
          </div>
        </div>
      
        <div style="margin-left:40px">
          <p class="heading">Coding rate</p>
          <div class="select">
            <select>
              <option>5</option>
              <option>1</option>
              <option>2</option>
              <option>3</option>
              <option>4</option>
            </select>
          </div>
        </div>
      </div>
    </nav>
    </div>


    <!-- lora info -->
    <div class="allSniffing">
      <div class="box" style="margin-top:20px;margin-bottom:20px;margin-left:20px;margin-right:20px">
        <article class="media">
          <div class="media-left">
            <figure class="image is-64x64">
              <img src="../assets/lora.png">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>MAC address:</strong> <small>f8:32:e4:f1:92:a3</small> 
                <br>
                <strong>protocol:</strong> <small></small>
                <br>
                <strong>payload:</strong> <small>{{info}}</small>
                <br>
                <strong>gps:</strong> <small>13.7660202,100.4526961,12z</small>
              </p>
            </div>
          </div>
        </article>
      </div>

            <div class="box" style="margin-top:20px;margin-bottom:20px;margin-left:20px;margin-right:20px">
        <article class="media">
          <div class="media-left">
            <figure class="image is-64x64">
              <img src="../assets/lora.png">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>MAC address:</strong> <small>a4:32:e4:f1:92:a3</small> 
                <br>
                <strong>protocol:</strong> <small></small>
                <br>
                <strong>payload:</strong> <small>{{info}}</small>
                <br>
                <strong>gps:</strong> <small>13.7660202,100.4526961,12z</small>
              </p>
            </div>
          </div>
        </article>
      </div>

            <div class="box" style="margin-top:20px;margin-bottom:20px;margin-left:20px;margin-right:20px">
        <article class="media">
          <div class="media-left">
            <figure class="image is-64x64">
              <img src="../assets/lora.png">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>MAC address:</strong> <small>b4:a5:e4:f1:92:a3</small> 
                <br>
                <strong>protocol:</strong> <small></small>
                <br>
                <strong>payload:</strong> <small>{{info}}</small>
                <br>
                <strong>gps:</strong> <small>13.7660202,100.4526961,12z</small>
              </p>
            </div>
          </div>
        </article>
      </div>
    </div>
    <!-- lora info -->


    <div id="result" style="color: SlateBlue; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{info}}
    </div>
    

  </div>
</template>

<script>
     // <ul>
      //   <li v-bind:for="item in info"><label>{{item.RSSI}}</label></li>
      // </ul>
// import LoraInfos from './components/loraInfo.vue';
import axios from 'axios';

// export default {
//   name: "home" ,
//   data () {
//     return {
//       info: 'loading....'
//     }
//   }
// };

export default {
  name: "home",
  data () {
    return {
      info: 'loading...'
    }
},
mounted () {
    console.log('hello')
    // https://192.168.4.1/lora
    // https://api.coindesk.com/v1/bpi/currentprice.json
    // if(this.info === null){
    //   this.info = 'loading.....'
    // }
    // setTimeout(()=>{
      axios
      .get('http://192.168.4.1/lora').then(res=>{
        console.log(res)
        // if(this.info === 'loading.....'){
        //   this.info = ''
        // }
        this.info = res.data
      })
    // },1000)
    
    
    // axios
    //   .get('http://192.168.4.1/lora').then(res=>{
    //     console.log(res)
    //     this.info = res.data
    //   })
      // .then(response => {
        // this.info = response.data
        // console.log(this.info)
        // })
      // .catch(err =>{
        // console.log(err)
      // })
  }

}


</script>
