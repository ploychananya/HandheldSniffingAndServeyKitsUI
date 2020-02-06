<template>
  <div class="home" style="background-color: hsl(0, 0%,95%);padding-bottom:100%;">

    <img alt="Iwing logo"  src="../assets/iwing.png" style="margin-top:50px;" />
    <!--<HelloWorld msg="Welcome to Your Vue.js App" />font-weight:bold
    
    -->
    <h1 style="font-size: 30px;font-family:sans-serif;">Handheld LoRa Survey & Sniffing Kits</h1>
    <br>
    <div style="background-color: hsl(210, 76%, 22%);padding-right:0px;padding-left:0px;padding-top:10px;padding-bottom:15px;margin-left:33px;margin-right:33px;">
    <nav class="level" >
      <div class="level-item has-text-centered">
        <div>
          <p style="color:white" class="heading">Frequency (MHz) </p><h5 style="color:red">{{cur_frequency}}</h5>
          <div class="select">
            <select  v-model="cur_frequency" @change="onFreChange($event)">
              <option>433</option>
              <option>169</option>
              <option>434</option>
              <option>866</option>
              <option>868</option>
              <option>915</option>
            </select>
          </div>

          
        </div>
      
     
        <div style="margin-left:50px">
          <p style="color:white" class="heading">Bandwidth (KHz)</p><h5 style="color:red">{{cur_bandwidth}}</h5>
          <div class="select">
            <select  v-model="cur_bandwidth" @change="onBWChange($event)">
              <option>125</option>
              <option>250</option>
              <option>20.8</option>
              <option>7.8</option>
              <option>15.6</option>
              <option>31.25</option>
            </select>
          </div>
      
        </div>
      </div>
      </nav>

      <nav class="level">
      <div class="level-item has-text-centered">
        <div>
          <p style="color:white" class="heading">Spreading factor</p><h5 style="color:red">{{cur_sf}}</h5>
          <div class="select">
            <select  v-model="cur_sf" @change="onSFChange($event)">
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
          <p style="color:white" class="heading">Coding rate</p><h5 style="color:red">{{cur_cr}}</h5>
          <div class="select">
            <select  v-model="cur_cr" @change="onCRChange($event)">
              <option>5</option>
              <option>1</option>
              <option>2</option>
              <option>3</option>
              <option>4</option>
            </select>
          </div>
        </div>
      
	  
<div style="margin-left:40px">
          <p style="color:white" class="heading">time interval (Sec)</p><h5 style="color:red">{{time_interval}}</h5>
          <div class="select">
            <select  v-model="time_interval" @change="onTIChange($event)">
              <option>0</option>
              <option>1</option>
              <option>2</option>
              <option>3.5</option>
              <option>3</option>
			  <option>4</option>
            </select>
          </div>
        </div>
    </div>
    <button @click="exportToCSV($event)" style="color:white;background:green;padding-top:5px;padding-bottom:5px;position: absolute;right:5%;font-size: 18px;margin-right:5px;margin-top:30px">Export to CSV</button>

    </nav>
    </div>

<!--
		<button style="width:95%;padding-top:0%;padding-bottom:0%;padding-left:0%;padding-right:0%;margin-top:20px;margin-bottom:0px;margin-left:20px;margin-right:20px" >
      <div class="box" style="background-color: hsl(156, 59%,60%);padding-top:15px;padding-bottom:15px;padding-left:0%;padding-right:0%;">
        <article class="media">
          <div class="media-left">
            <figure class="image is-128x128">
              <img src="../assets/lora.png">
            </figure>
          </div>


          <div class="media-content">
			

            <div class="content" style="font-size: 18px;">
			
              <p>

				<b-switch alight="right" v-model="isSwitchedCustom"
					true-value="Sound On"
					false-value="Sound Off">
					{{ isSwitchedCustom }}
				</b-switch><br>
				<strong>updated time:</strong> <small style="font-size: 20px;" ></small> 
				<br>
				<strong>format:</strong> <small style="font-size: 20px;"></small> 
				<br>
                <strong>mac address:</strong> <small style="font-size: 20px;"></small> 
                <br>
                <strong>data:</strong> <small style="font-size: 20px;"></small>
                <br>
                <strong>rssi:</strong> <small style="font-size: 20px;"></small>
                <br>
				<strong>snr:</strong> <small style="font-size: 20px;"></small>
                <br>
                <strong>gps:</strong> <small style="font-size: 20px;"></small>
			
              </p>
            </div>
          	</div>
        	</article> 
     		</div>
		</button>
    -->
    
<!--
	 <h3 v-html="arrayJsonLoRa" id="resul3" style="color: green; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arrayJsonLoRa}}
    </h3>

	 <h3 v-html="arrayOtherLoRa" id="resul3" style="color: green; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arrayOtherLoRa}}
    </h3> 
	
	
	v-on="click : clickHandler"

			<button  v-for="lora in arrayJsonLoRa" v-bind:key="lora.macAddr"  
      style="width:95%;padding-top:0%;padding-bottom:0%;padding-left:0%;padding-right:0%;
      margin-top:20px;margin-bottom:0px;margin-left:20px;margin-right:20px" >
		</button>
      <div  v-for="lora in arrayJsonLoRa" v-bind:key="lora.macAddr" class="box" style="align=center;width:95%;
padding-right:0px;padding-left:0px;padding-top:10px;padding-bottom:10px;margin-left:33px;margin-right:33px;
      <div  v-for="lora in arrayJsonLoRa" v-bind:key="lora.macAddr" class="box" style="align=center;width:95%;



//////////////////////////////
<button v-for="lora in arrayOtherLoRa" v-bind:key="lora.macAddr" style="width:95%;padding-top:0%;padding-bottom:0%;padding-left:0%;padding-right:0%;margin-top:20px;margin-bottom:0px;margin-left:20px;margin-right:20px" >
        <div class="box" style="background-color: hsl(41, 80%,60%);padding-top:15px;padding-bottom:15px;padding-left:0%;padding-right:0%;">
-->
	
    <div  v-for="(lora,index) in arrayJsonLoRa" v-bind:key="lora.macAddr" class="box" style="
      background-color: hsl(156, 59%,60%);padding-right:0px;padding-left:0px;padding-top:10px;
      padding-bottom:5px;margin-left:33px;margin-right:33px;margin-top:20px;margin-bottom:0px;">
        <article class="media">
          <div class="media-left">
            <figure class="image is-128x128">
              <img src="../assets/lora.png">
            </figure>

          </div>
          
          <div class="media-body">
            <div class="content" style="font-size: 18px;">
            
              <p>
			  	
				<strong>updated time:</strong> <small style="font-size: 20px;" >{{lora.timeUpdate}}</small> 
                <br>
				<strong>format:</strong> <small style="font-size: 20px;">{{lora.format}}</small> 
				<br>
                <strong>mac address:</strong> <small style="font-size: 20px;">{{lora.macAddr}}</small> 
                <br>
                <strong>data:</strong> <small style="font-size: 20px;">{{lora.data}}</small>
                <br>
                <strong>rssi:</strong> <small style="font-size: 20px;">{{lora.rssi}}</small>
                <br>
				<strong>snr:</strong> <small style="font-size: 20px;">{{lora.snr}}</small>
                <br>
                <strong>gps:</strong> <small style="font-size: 20px;">{{lora.gps}}</small>
			
              </p>
            </div>

          	</div>
            <div class="media-right" style="position: absolute;right:5%;font-size: 18px;margin-right:5px;margin-top:5px">
              <div>
                <strong style="margin-right:20px">sound:</strong><br>
                <button @click="onClick($event,index,++count,lora.format)" style="background: white;padding-left:0px;padding-right:0px;padding-top:0px;padding-bottom:0px">
                    <img class="image is-64x64" v-bind:id="index" src="../assets/soundOff.png" style="background:white;" />
                </button>
              </div>
              <div style="margin-top:0px">
                <strong style="margin-right:5px">statistic:</strong><br>
                <button style="background-color: blue;padding-left:0px;padding-right:0px;padding-top:0px;padding-bottom:0px">
                    <img class="image is-64x64" src="../assets/analysis.png"/>
                </button>
              </div>
            </div>

        	</article> 
     		</div>

		 <div  v-for="(lora,index) in arrayOtherLoRa" v-bind:key="lora.macAddr" class="box" style="
      background-color: hsl(41, 80%,60%);padding-right:0px;padding-left:0px;padding-top:10px;
      padding-bottom:30px;margin-left:33px;margin-right:33px;margin-top:20px;margin-bottom:0px;">
        <article class="media">
          <div class="media-left">
            <figure class="image is-128x128">
              <img src="../assets/lora.png">
            </figure>
          </div>
          <div class="media-body" style="font-size: 18px;">
            <div class="content">
              <p>
			  
			  	<strong>updated time:</strong> <small style="font-size: 20px;">{{lora.timeUpdate}}</small> 
                <br>
                <strong>format:</strong> <small style="font-size: 20px;"> {{lora.format}}</small>
                <br>
                <strong>data:</strong> <small style="font-size: 20px;">{{lora.data}}</small>
                <br>
				<strong>rssi:</strong> <small style="font-size: 20px;">{{lora.rssi}}</small>
                <br>
				<strong>snr:</strong> <small style="font-size: 20px;">{{lora.snr}}</small>
                <br>
                <strong>gps:</strong> <small style="font-size: 20px;">{{lora.gps}}</small>
              </p>
            </div>
          </div>

           <div class="media-right" style="position: absolute;right:5%;font-size: 18px;margin-right:5px;margin-top:0px">
              <div>
              <strong style="margin-right:20px">sound:</strong><br>
                <button @click="onClick($event,index,++count,lora.format)" style="background: white;padding-left:0px;padding-right:0px;padding-top:0px;padding-bottom:0px">
                    <img class="image is-64x64" v-bind:id="index" src="../assets/soundOff.png" style="background:white;" />
                </button>
              </div>
              <div style="margin-top:0px">
                <strong style="margin-right:5px">statistic:</strong><br>
                <button style="background-color: blue;padding-left:0px;padding-right:0px;padding-top:0px;padding-bottom:0px">
                    <img class="image is-64x64" src="../assets/analysis.png"/>
                </button>
              </div>
            </div>


        </article>
      </div>

	<h3 v-html="info" id="result" style="color: SlateBlue; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{info}} <br>
    </h3>

    <h3 v-html="in_gps" id="result2" style="color: red; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{in_gps}}
    </h3>

    <h3 v-html="input" id="resul3" style="color: green; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{input}}<br>
    </h3>

	<h3 v-html="arrayJsonMac" id="resul3" style="color: green; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arrayJsonMac}}<br>
    </h3>
	<h3 v-html="arrayJsonLoRa" id="resul3" style="color: green; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arrayJsonLoRa}}<br>
    </h3>
	<h3 v-html="arrayOtherMac" id="resul3" style="color:orange; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arrayOtherMac}}<br>
    </h3>
	<h3 v-html="arrayOtherLoRa" id="resul3" style="color: orange; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arrayOtherLoRa}}<br>
    </h3>

    <h3 v-html="arraylog" id="resul3" style="color: orange; font-size: 200%; font-family: Monaco, monospace; margin: 20px">
      {{arraylog}}<br>
    </h3>

  </div>
</template>

<script>
     // <ul>
      //   <li v-bind:for="item in info"><label>{{item.RSSI}}</label></li>
      // </ul>
// import LoraInfos from './components/loraInfo.vue';
import axios from 'axios';
      // CSV_log:"data:text/csv;charset=utf-8," + this.arraylog.map(e => e.join(",")).join("\n"),
// 
export default {
  name: "home",
  data () {
    return {
      arrayJsonLoRa:[],
      arrayOtherLoRa:[],
      arrayJsonMac:[],
      arrayOtherMac:[],
      arraylog:[],
      info: 'loading...',
      in_gps: 'gps loading...',
      input: 'hello',
      cur_frequency: 433,
      cur_sf: 7,
      cur_cr: 5,
      cur_bandwidth:125,
	  time_interval:3.5,
    count:0,
    beep_beep:null,
    check:null,
    audio :new Audio(require('./../assets/tick.mp3'))
    }
  },
  mounted () {
    var JsonStruct = 
	{	macAddr: "",
		format:"JSON",
		data:"",
		rssi:"",
		gps:"",
		snr:"",
		timeUpdate:"" 
	}
	var OtherStruct = {
		data:"",
		rssi:"",
		snr: "",
		gps: "",
		format: "OTHER",
		timeUpdate:""
	}
    const self = this;
    let main_setInterval = window.setInterval(async ()=>{ 
		
    let currentDate = new Date();
    let str_currentDate = this.fillZero(currentDate.getFullYear())+'-'+this.fillZero(currentDate.getMonth()+1)+'-'+this.fillZero(currentDate.getDate())+' '+
      this.fillZero(currentDate.getHours())+':'+this.fillZero(currentDate.getMinutes())+':'+this.fillZero(currentDate.getSeconds());

		var _lora = await axios.get('http://192.168.4.1/lora').then((res)=>{
			// console.log(res.data)
			// console.log(res)
			let input = JSON.parse(JSON.stringify(res.data))
			self.info = input;
			return input

		})

	  	//get gps data
		var _gps = await axios.get('http://192.168.4.1/gps').then(res => res.data)
		// {
          	// console.log(res.data)
			// // console.log("index that mac ="+ input.macAddr+"  is "+ index)
          	// let input = JSON.parse(JSON.stringify(res.data))
          	// self.gps = input.status
					
			// arrayJsonLoRa[index].gps= input.status;
        // }
		// )
		self.in_gps = _gps.status

		// console.log("_lora is ============= "+ _gps.status)

    if(_lora.status==="success"){
      //logging
      self.arraylog.push(
        {
          timeStamp: str_currentDate,
          data: _lora,
          gps: _gps
        }
      )
	  
      if(_lora.payload['macAddr']!== undefined && self.arrayJsonLoRa.findIndex(obj => obj.macAddr === _lora.payload['macAddr'])>=0){
        let index = self.arrayJsonLoRa.findIndex(obj => obj.macAddr === _lora.payload['macAddr'])
        // console.log("index that mac ="+ _lora.payload['macAddr']+"  is "+ index)
        if(index>=0){
          self.arrayJsonLoRa.splice(index,1)
          self.arrayJsonLoRa.splice(0,0, {
          macAddr:_lora.payload['macAddr'],
          data:_lora.payload['data'],
          rssi:_lora.rssi,
          snr: _lora.snr,
          gps: _gps.status,
          format: "JSON",
          timeUpdate:str_currentDate
          })
        }
       
      }else if(_lora.payload['macAddr']!==undefined && self.arrayJsonLoRa.findIndex(obj => obj.macAddr === _lora.payload['macAddr'])<0){
        self.arrayJsonMac.push(_lora.payload['macAddr'])
        self.arrayJsonLoRa.splice(0,0, {
          macAddr:_lora.payload['macAddr'],
          data:_lora.payload['data'],
          rssi:_lora.rssi,
          snr: _lora.snr,
          gps: _gps.status,
          format: "JSON",
          timeUpdate:str_currentDate
        })
     
      }else if(_lora.payload['macAddr']==undefined && self.arrayOtherLoRa.findIndex(obj => obj.data === _lora.payload)>=0){ //other format
        let index = self.arrayOtherLoRa.findIndex(obj => obj.data === _lora.payload)
        // console.log("index that mac ="+ (_lora.payload).substring(16,21)+"  is "+ index)
        if(index>=0){
          self.arrayOtherLoRa.splice(index,1)
          self.arrayOtherLoRa.splice(0,0, {
          data:_lora.payload,
          rssi:_lora.rssi,
          snr: _lora.snr,
          gps: _gps.status,
          format: "OTHER",
          timeUpdate:str_currentDate
          })
          // self.arrayOtherLoRa.splice(index,1)
        }
       
      }else if(_lora.payload['macAddr']==undefined && self.arrayOtherLoRa.findIndex(obj => obj.data === _lora.payload)<0){
        self.arrayOtherMac.push((_lora.payload).substring(16,21))
        //insert to the first one
        self.arrayOtherLoRa.splice(0,0, {
          data:_lora.payload,
          rssi:_lora.rssi,
          snr: _lora.snr,
          gps: _gps.status,
          format: "OTHER",
          timeUpdate:str_currentDate
        })
      
      }
    }
		

    },(this.time_interval*1000))

// get value just when starting
    axios
    .get('http://192.168.4.1/params')
    .then(res => {
      console.log(res.data)
      self.cur_frequency= res.data.frequency;
      self.cur_sf= res.data.sf;
      self.cur_cr= res.data.coding_rate;
      self.cur_bandwidth=(res.data.bw/1000);
      this.input = res.data
    })
    

      
  },
  methods: {
    fillZero:(n)=>{
      if(n<10) return "0"+n ;
      else return n; 
    },
    equalObjectValue:(element) => {element==_lora.payload.macAddr},
      setParam:  (type,value) => {
        axios.get('http://192.168.4.1/set/'+type+'/'+value,{'Access-Control-Allow-Origin':'*','content-type':'application/json'})
        .then(res=>{
          // console.log(res.data)
          this.input = res.data
        })
      },
      onFreChange(event) {
        axios.get('http://192.168.4.1/set/frequency/'+event.target.value,{'Access-Control-Allow-Origin':'*','content-type':'application/json'})
        .then(res=>{
          // console.log(res.data)
          this.input = res.data
        })        
      },
      onBWChange(event) {
        let bw = event.target.value*1000
        axios.get('http://192.168.4.1/set/bandwidth/'+bw,{'Access-Control-Allow-Origin':'*','content-type':'application/json'})
        .then(res=>{
          // console.log(res.data)
          this.input = res.data
        })        
      },
      onSFChange(event) {
        axios.get('http://192.168.4.1/set/spreading_factor/'+event.target.value,{'Access-Control-Allow-Origin':'*','content-type':'application/json'})
        .then(res=>{
          // console.log(res.data)
          this.input = res.data
        })        
      },
      onCRChange(event) {
        axios.get('http://192.168.4.1/set/coding_rate/'+event.target.value,{'Access-Control-Allow-Origin':'*','content-type':'application/json'})
        .then(res=>{
          // console.log(res.data)
          this.input = res.data
        })       
      },
    onTIChange(event){
      this.time_interval =  event.target.value
    },
    onClick(event,index,count,type){
      console.log(event.target.src)
      let sound_On = count%2===1?true:false
      this.audio.playbackRate = 1

      if(sound_On){
        this.check = true
        console.log("click")
        event.target.style.background = "yellow";
        event.target.src = require('./../assets/soundOn.png');
        var time = 1000;
        this.beep_beep = window.setInterval(()=>{ 
          var rssi = -164
          if(type==="JSON"){
            rssi = this.arrayJsonLoRa[index].rssi
          }else{
            rssi = this.arrayOtherLoRa[index].rssi
          }
          console.log("rssi==="+rssi)
          if(rssi<=-90){//very bad
            // this.time=4000
            this.audio.playbackRate = 0.1
          }else if(rssi<=-70){
            // this.time=3000
            this.audio.playbackRate = 0.25
          }else if(rssi<=-50){
            // this.time=2000
            this.audio.playbackRate = 0.5
          }else if(rssi<=-30){
            // this.time=1000
            this.audio.playbackRate = 3.5
          }else{
            // this.time=500
            this.audio.playbackRate = 6.8
          }
          console.log("time== "+this.time)
          this.audio.play();
        },this.time)
        
      }else{
        console.log("clear")
        this.audio.playbackRate = 1
        clearInterval(this.beep_beep);
        event.target.style.background = "white";
        event.target.src = require('./../assets/soundOff.png');
        // "http://localhost:8080/img/soundOff.de9eb7c1.png"
      }
        

    },
    exportToCSV(event){
      let csvContent = "data:text/csv;charset=utf-8,"
      this.arraylog.forEach((rowArray)=> {
        let row = rowArray['timeStamp']+","
        row += (rowArray.data.payload['macAddr']===null?null:rowArray.data.payload['macAddr'])+","
        row +=(rowArray.data.payload['data']===null?rowArray.data.payload:rowArray.data.payload['data'])+","
        row +=rowArray.data.rssi + "," + rowArray.data.snr + ","
        row +=(rowArray.gps.status==="success"?(rowArray.gps.status+","+rowArray.gps.latitude+","+rowArray.gps.longitude).toString():(rowArray.gps.status+","+null+","+null).toString())
        csvContent += row + "\r\n";
      });
      let encodedUri = encodeURI(csvContent);
      window.open(encodedUri);
    }
  }

}


</script>
