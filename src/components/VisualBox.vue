<template>
<div>
<p>3D model placeholder for real data </p>

<div>

<button @click="sampleone = !sampleone">show data sample 1</button>


<button @click="sampletwo = !sampletwo">show data sample 2</button>

<div v-if="sampleone" id="DemoOne">
<b>data sample 1 </b>

green squares represents 20 units of small square solar panels on (120*120) geometric plane space

<img height="400" width="400" src="./sampleOneData.gif" >
</div>

<div v-if="sampletwo" id="DemoTwo">
<b> data sample 2 </b>

green squares represents 20 units of rectangular panels on (120*120) geometric plane space

<img height="400" width="400" src="./sampleTwoData.gif" >
</div>


</div>



</div>
</template>

<script>
export default {
  data() {
  	return {
	    sampleone: false,
      sampletwo:false
  	}
	}
}
</script>

<style>
</style>