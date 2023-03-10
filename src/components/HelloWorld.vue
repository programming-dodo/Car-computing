<script setup lang="ts">
import { ref, computed } from 'vue';

const myChoiceWheels = ref('');
const myChoiceBody = ref('');
const myChoiceEngine = ref('');
const myChoiceCourse = ref ('');

interface carType {
  speed: number;
  weight: number;
  terrainGround: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
}
const cartype = [];

const cars: carType[] = [];

interface carbody {
  body: string;
  wheel: wheel;
  engine: string;
}
interface wheelOptions {
  name: string;
  speed: number;
  weight: number;
  terrainGround: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
}
interface bodyOptions {
  name: string;
  speed: number;
  weight: number;
  terrainGround: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
  
}

interface engineOptions {
  name: string;
  speed: number;
  weight: number;
  terrainGround: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
}

interface courseOptions {
  name: string;
  length: number;
  terrainGround: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
}

const carbody = [];

const wheel = [];

const wheelOptions: wheel[] = [
  {
    name: 'wings',
    speed: 12,
    weight: 0,
    terrainGround: false,
     terrainWater: false,
      terrainAir: true,
  },
  {
    name: 'grippers',
    speed: 9,
    weight: 1,
    terrainGround: true,
     terrainWater: false,
      terrainAir: false,
  },
  {
    name: 'paddle wheels',
    speed: 4,
    weight: 2,
    terrainGround:false,
     terrainWater:true,
      terrainAir: false,
  },
];

const body = [];

const bodyOptions: body[] = [
  {
    name: 'bullet',
    speed: 12,
    weight: 0,
    terrainGround:false,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'dodomobile',
    speed: 10,
    weight: 1,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'Boulder',
    speed: -40,
    weight: 20,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
    
  },
];

const engine = [];

const engineOptions: engine[] = [
  {
    name: 'cheetah',
    speed: 15,
    weight: 0,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'lockness',
    speed: 10,
    weight: 1,
    terrainGround:false,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'dragonFueled',
    speed: 12,
    weight: 2,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
];

const courseOptions: course[] = [
  {
    name: 'desert',
    length:600,
    terrainGround: true,
    terrainWater: false,
    terrainAir: false,
  },
  {
    name: 'ocean',
    length: 600,
    terrainGround: false,
    terrainWater: true,
    terrainAir: false,
  },
  {
    name: 'clouds',
    length: 600,
    terrainGround: false,
    terrainWater: false,
    terrainAir: true,
  },
]

const myCarGroundTerrain = computed(() =>
{
  let myCarAbleGround = false
  if (myChoiceBody.value.terrainGround | myChoiceWheels.value.terrainGround  ) {
    myCarAbleGround =  true
  } else {
    myCarAbleGround= false
  } return myCarAbleGround
})
const myCarWaterTerrain = computed(() =>
{
  let myCarAbleWater = false
  if (myChoiceBody.value.terrainWater | myChoiceWheels.value.terrainWater  ) {
    myCarAbleWater =  true
  } else {
    myCarAbleWater = false
  } return myCarAbleWater
})
const myCarAirTerrain = computed(() =>
{
  let myCarAbleAir = false
  if (myChoiceBody.value.terrainAir | myChoiceWheels.value.terrainAir  ) {
    myCarAbleAir =  true
  } else {
    myCarAbleAir = false
  } return myCarAbleAir
})

const myCourseWater = computed(() => {

  if (myChoiceCourse.value.terrainWater === true && myCarWaterTerrain.value === false) {
   return false
 } else if (myChoiceCourse.value.terrainAir === true && myCarAirTerrain.value === false) {
   return false
 } else if (myChoiceCourse.value.terrainGround === true && myCarGroundTerrain.value === false) {
   return false
 } else{
   return true
 }
})


const myCarSpeed = computed(() => {
  let speedDisplay = 'error';
  let totalSpeed =
    myChoiceWheels.value.speed +
    myChoiceEngine.value.speed +
    myChoiceBody.value.speed;

  if (totalSpeed <= 0) {
    speedDisplay = '0';

  } else {
    speedDisplay = totalSpeed;
  }

 
  return speedDisplay;
});
const myWheelsType = computed(() => {
  let weight = 'Car incomplete!';
  let total =
    myChoiceWheels.value.weight +
    myChoiceEngine.value.weight +
    myChoiceBody.value.weight;
  if (total > 3) {
    weight = 'heavy';
  } else if (total == 3) {
    weight = 'medium';
  } else if (total == 2) {
    weight = 'medium';
  } else if (total == 1) {
    weight = 'medium';
  } else if (total == 0) {
    weight = 'light';
  }
  
  return weight;
});

function myCarComplete () 
{ 
   if ( myChoiceEngine.value?.name === undefined | myChoiceWheels.value?.name === undefined | myChoiceBody.value?.name === undefined  ) {
     window.alert('car incomplete')
   } else if( myChoiceBody.value.name === "Boulder") {
     window.alert(' Its a Boulder THEY DONT MOVE')
   } else if (myChoiceCourse.value.name === undefined){
     window.alert ('no course selected')
   } else if (myCourseWater.value === false ){
     window.alert('car canot drive on this terrain')
   } else {
     window.prompt(' You won :D : enter you name so we can add you to the leaderboard')
   } 
}
</script>

<template>
  <p>
    speed:
    {{ myCarSpeed }}
  </p>
  <p>weight: {{ myWheelsType }}</p>
  <p>terrain<hr/>ground: {{ myCarGroundTerrain }}
  <br>Water:{{ myCarWaterTerrain }}
 <br>Air:{{  myCarAirTerrain}}</p>
  <select v-model="myChoiceWheels">
    <option disabled hidden value="">select wheel</option>
    <option v-for="Wheels in wheelOptions" :key="Wheels.name" :value="Wheels">
      {{ Wheels.name }}
    </option>
  </select>
  <hr />
  <select v-model="myChoiceEngine">
    <option disabled hidden value="">select engine</option>
    <option v-for="engine in engineOptions" :key="engine.name" :value="engine">
      {{ engine.name }}
    </option>
  </select>
  <hr />
  <select v-model="myChoiceBody">
    <option disabled hidden value="">select body</option>
    <option v-for="body in bodyOptions" :key="body.name" :value="body">
      {{ body.name }}
    </option>
  </select>
  <hr/>
    <h2>Race courses</h2>
    <select  v-model = "myChoiceCourse">
    <option disabled hidden value=''>select race course</option>
    <option v-for="course in courseOptions" :key="course.name" :value="course">
      {{ course.name }}
    </option>
    </select>

    <button @click= "myCarComplete()"> race</button>
    <hr>
    Ground:{{myCourseGround}}<br>
    Water:{{myCourseWater}}<br>
    Air:{{myCourseAir}}<br>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
