<template>
  <div id="app">
            <v-btn color="blue darken-1" text @click="btnClick($event)">LED ON</v-btn>
            <v-btn color="blue darken-1" text @click="btnClick($event)">LED OFF</v-btn>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data () {
        return {
            urlinfo:'http://localhost:8000/devices/',
            urldevice:'http://220.81.195.192:5000/led' 
        }
    },
    created(){
        this.$bus.$on('deviceSelected',this.refleshData)
    },
    methods: {
        refleshData(data) {
            axios.get(this.urlinfo+data.deviceId) //서버에 요청하기
            .then((res) => {
                console.log(res.data); //성공시
                this.items = res.data;
            })
            .catch((err) => {
                alert('에러 발생: ' + err); //에러 발생
            });          
        },
        btnClick($event){
            if($event.target.innerHTML == "LED ON"){
                axios.get(this.urldevice+'?state=on');      
            }
            if($event.target.innerHTML == "LED OFF"){
                axios.get(this.urldevice+'?state=off');    
            }
        }
  }
}
</script>
<style scoped>
  div{
    margin:0 5px 0 5px;
  }
</style>