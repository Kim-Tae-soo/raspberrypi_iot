<template>
    <div id="current-weather">
        <div class="location">{{location}}</div>
        <div class="weather">{{weather}}</div>
        <div class="temperature">{{temperature}}℃</div>
    </div>
</template>
<script>
    export default {
        name: 'current-weather',
        data(){
            return{
                location:'',
                weather:'',
                temperature:0,
                lat:37.566535,
                lng:126.977969
            }
        },
        created(){
            this.$bus.$on('deviceSelected',this.refleshData)
        },
        methods: {
            refleshData(data) {
                this.lat = data.latitude    //전달된 좌표 값 수신
                this.lng = data.longitude
                this.axios.get(`http://api.openweathermap.org/data/2.5/weather?lat=${this.lat}&lon=${this.lng}&appid=67c78818c6afe50f6425fa397c98a955`)
                .then((response)=>{
                    let data = response.data
                    this.location = data.name
                    this.weather = data.weather.main
                    this.temperature = (data.main.temp-273.15).toFixed(0)
                })
                .catch((error)=>{
                    console.log(error)
                })                
            }
        }
    }
</script>
<style scoped>
	.location {
		text-align : center;
		font-size : 40pt;
		color : black;
	}
	.weather{
		text-align : center;
		font-size : 20pt;
		font-weight : 100;
		color : black;
	}
	.temperature{
		text-align : center;
		font-size : 50pt;
		font-weight : 100;
		color : black;
	}
</style>