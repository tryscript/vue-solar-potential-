<template>
<div>
<h5> we are calculating per year total consumption</h5>

<h5> assuming number of solar units [var2] covers 100 square foot </h5>

<br>
<br>
<p>var1 - required Energy usage <b>{{EnergyUsage}}</b>  Kwh Per year : </p>
<input v-model="EnergyUsage" >
<!--average US for 2020 is 10715 kwh per resident  -->
<br>
<br>
 <p>var2 - number of Solar units (panels or solar cells): <b>{{SolarUnit}}</b></p>
<input v-model="SolarUnit">
<br>
<br>
 <p>var3 -efficiency per unit in Watts <b>{{effiencyUnit}}</b></p>
<input v-model="effiencyUnit">
<br>
<br>
 <p>(vars 4,5) dimentions of -each unit solar cell / panel </p>
 <br>
W :{{Width}}<input v-model="Width">
<br>
<br>
L :{{Length}}<input v-model="Length">
<br>
<br>
 <p>var6 - number of solar hours per year for location . 
 
 <p class="grey">hours input can be taken from <a href="https://sunroof.withgoogle.com/"> Google solar roof </a> </p>
 <input v-model="sunInput">
<br>
<br>
<button id="FinalCalc" @click="solarCalc()">Calculate</button>

<div id="outputBox">

space required to  match energy demand [Var1]

<br>
<h2><div id="sqSpaceValue"></div> * 100 square foot</h2>

</div>


</div>




</div>
</template>

<script>


export default {
  components: {
   
  },
  data () {
    return {
  sqSpaceValue:'',
  EnergyUsage:0,
  SolarUnit:0,
effiencyUnit:0,
Width:0,
Length:0,
sunInput:0,
    }
  },
  async created () {
     

  },
  
  methods: {

    async solarCalc(){

      // UI input 
 let varEng = this.EnergyUsage ;
 let Sunit = this.SolarUnit;
let Eunit = this.effiencyUnit;
let sunHours = this.sunInput;

// Calc logic 

//our Calculator logic 

 // energy needed / energy generated = x unit of space required (*100 Square foot )

 // energy needed in a year = UI input Kwh (var1)

//Energy generated = hours of sunlight per year * effiency in watts * units of solar * 0.75 ( for general temp and energy fluctuations) / 1000 = kwh generated 
//Energy generated = ( var6* var3 * var2 * 0.75 ) = (energy in watts ) / 1000 = energy in kwh 


let EngGeneratedinWatts = sunHours * Sunit * Eunit  * 0.75 ;
let EngGeneratedinKwh = EngGeneratedinWatts / 1000 ;

let SquareFootSpace = varEng / EngGeneratedinKwh ;

let  sqSpaceValue = Math.round( SquareFootSpace) ;

 document.getElementById("sqSpaceValue").innerHTML = sqSpaceValue ;
//return sqSpaceValue;

// console tests 
      console.log("calc started:");
      console.log("user selected: " + varEng + "energy required in Kwh");
      console.log("EngGenerated :" +  EngGeneratedinWatts + "Watts ");
      console.log("EngGenerated :" + EngGeneratedinKwh  + "Kwh ");
      console.log("SquareFootSpace :" +  sqSpaceValue);
// //  expected behavior 
// sample data 1 10 watts 
// input 
if (varEng == 4800 & sunHours == 2000 & Sunit == 10 & Eunit == 10 & SquareFootSpace == 32 ){
  console.log("passes sample data 1 test")
}
else if (varEng == 4800 & sunHours == 2000 & Sunit == 10 & Eunit == 10 & SquareFootSpace !== 32)
{console.log("fails sample data 1 test")}
    
    else if (varEng + sunHours +  Sunit + Eunit < 100)
{console.log("data is not suffient to run sample 1 test ")}

// //  expected behavior 
// sample data 2
// input 
// - varEng = 4800 
//sunHours= 2000
//  Sunit =78 
// Eunit =1 watt only 
// SquareFootSpace output should be  = 41
if (varEng == 4800 & sunHours == 2000 & Sunit == 78 & Eunit == 1 & sqSpaceValue == 41  ){
  console.log("passes sample data 2 test")
}
else if (varEng == 4800 & sunHours == 2000 & Sunit == 78 & Eunit == 1 & sqSpaceValue !==  41)
{console.log("fails sample data 2 test")}

// //  expected behavior 
// sample data 3
// input 
// - varEng = 4800 
//sunHours= 2000
//  Sunit = 13
// Eunit = 9 watts 
// SquareFootSpace output should be  = 27
if (varEng == 4800 & sunHours == 2000 & Sunit == 13 & Eunit == 9 & sqSpaceValue == 27 ){
  console.log("passes sample data 3 test")
}
else if (varEng == 4800 & sunHours == 2000 & Sunit == 13 & Eunit == 9 & sqSpaceValue !== 27)
{console.log("fails sample data 3 test")}


// //  expected behavior 
// sample data 4
// input 
// - varEng = 4800 
//sunHours= 2000
//  Sunit = 1
// Eunit = 100 watts 
// SquareFootSpace output should be  = ???
if (varEng == 4800 & sunHours == 2000 & Sunit == 13 & Eunit == 100 & sqSpaceValue == 32 ){
  console.log("passes sample data 4 test")
}
else if (varEng == 4800 & sunHours == 2000 & Sunit == 13 & Eunit == 100 & sqSpaceValue !== 32)
{console.log("fails sample data 4 test")}


// //  expected behavior 
// sample data 5
// input 
// - varEng = 4800 
//sunHours= 2000
//  Sunit = 300
// Eunit = 0.3 watts 
// SquareFootSpace output should be  = 36
if (varEng == 4800 & sunHours == 2000 & Sunit == 300 & Eunit == 0.3 & sqSpaceValue == 36 ){
  console.log("passes sample data 5 test")
}
else if (varEng == 4800 & sunHours == 2000 & Sunit == 300 & Eunit == 0.3 & sqSpaceValue !== 36 )
{console.log("fails sample data 5 test")}


    }
  }
  ,
  mounted(){
  
  },
}

</script>

<style>
.grey{
    color:grey
}
#outputBox{
border-style: solid;
margin:20px; 
padding:20px; 
}
</style>
