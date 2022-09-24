<template>
  <div class="hello">
 <div class="container text-center">




  <div class="row">
  <!---part A calc section -->
    <div class="col"> <p>Calculating </p><div id="CalcBox"><solarCalc /></div>  </div>

    
<div class="col"><img height="300px" src="https://images.unsplash.com/photo-1582614378336-15327b1f6a0d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80"></div>
<!---part B threejs section -->
    <div class="col"> <p>visualizing</p><div id="threejsBox">
    <VBox/>
    </div></div>
</div>



<div class="footer"></div>



  </div>
</div>
</template>

<script>
import solarCalc from "./SolarCalc.vue"
import VBox from "./VisualBox.vue"
export default {
  components: {
    solarCalc,
    VBox
  },
  data () {
    return {
     
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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
  color: #35495E;
}
.footer{
  margin: 30px;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #fc6f03;
  color: black;
}
</style>
