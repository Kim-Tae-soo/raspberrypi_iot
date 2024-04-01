<template>
<div>
	<div id = "map-canvas"/>
</div>
</template>

<script>
	export default {
		name: 'map-canvas',
        created(){
            this.$bus.$on('deviceSelected',this.refleshData)
        },
        methods: {
            refleshData(data) {
                var center = new google.maps.LatLng(data.latitude,data.longitude)
                new google.maps.Map(document.getElementById('map-canvas'), {
                    center : center,
                    zoom: 12
                })        
            }
        }
}</script>

<style scoped>
	#map-canvas{
		width: 800px;
		height: 300px;
	}
</style>