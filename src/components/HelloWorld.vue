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
    name: 'Grippers',
    speed: 9,
    weight: 1,
    terrainGround: true,
     terrainWater: false,
      terrainAir: false,
  },
  {
    name: 'Springs',
    speed: 11,
    weight: 1,
    terrainGround: true,
     terrainWater: false,
      terrainAir: false,
  },
  {
    name: 'Sneakers',
    speed: 8,
    weight: 0,
    terrainGround: true,
     terrainWater: false,
      terrainAir: false,
  },
  {
    name: 'Spike Balls',
    speed: 13,
    weight: 3,
    terrainGround: true,
     terrainWater: false,
      terrainAir: false,
  },
  {
    name: 'Paddle wheels',
    speed: 4,
    weight: 1,
    terrainGround:true,
     terrainWater:true,
      terrainAir: false,
  },
  {
    name: 'Propellors',
    speed: 12,
    weight: 2,
    terrainGround:false,
     terrainWater:true,
      terrainAir: false,
  },
  {
    name: 'Hydro Boosters',
    speed: 17,
    weight: 2,
    terrainGround:false,
     terrainWater:true,
      terrainAir: false,
  },
  {
    name: 'All terrain',
    speed: 3,
    weight: 1,
    terrainGround: true,
     terrainWater: true,
      terrainAir: true,
  },
  {
    name: 'Wings',
    speed: 12,
    weight: 0,
    terrainGround: false,
     terrainWater: false,
      terrainAir: true,
  },
  {
    name: 'Thrusters',
    speed: 12,
    weight: 0,
    terrainGround: false,
     terrainWater: false,
      terrainAir: true,
  },
  {
    name: 'Sneakers',
    speed: 8,
    weight: 0,
    terrainGround: true,
     terrainWater: false,
      terrainAir: false,
  },
];

const body = [];

const bodyOptions: body[] = [
  
  {
    name: 'Dodomobile',
    speed: 10,
    weight: 1,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'Boulder',
    speed: -100,
    weight: 20,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  
  {
    name: 'Scooter',
    speed: 8,
    weight: 1,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'Motorcycle',
    speed: 15,
    weight: 2,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  
  {
    name: 'SailBoat',
    speed: 10,
    weight: 1,
    terrainGround:false,
     terrainWater:true,
      terrainAir: false,
  },
  
  {
    name: 'Submarine',
    speed: 13,
    weight: 1,
    terrainGround:false,
     terrainWater:true,
      terrainAir: false,
  },
  {
    name: 'Schooner',
    speed: 9,
    weight: 0,
    terrainGround:false,
     terrainWater:true,
      terrainAir: false,
  },
  {
    name: 'AirCraftCarrier',
    speed: 5,
    weight: 1,
    terrainGround:false,
     terrainWater:true,
      terrainAir: true,
  },
  {
    name: 'Bullet',
    speed: 12,
    weight: 0,
    terrainGround:false,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'HoverBoard',
    speed: 12,
    weight: 0,
    terrainGround:false,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Zeplin',
    speed: 10,
    weight: 3,
    terrainGround:false,
     terrainWater:false,
      terrainAir: true,
  },
];

const engine = [];

const engineOptions: engine[] = [
  {
    name: 'Cheetah',
    speed: 15,
    weight: 0,
    terrainGround:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'Lockness',
    speed: 10,
    weight: 1,
    terrainGround:false,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'DragonFueled',
    speed: 12,
    weight: 2,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Antigravity',
    speed: 16,
    weight: -2,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Cyberpunk',
    speed: 10,
    weight: 1,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Kryptonite',
    speed: 14,
    weight: 0,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Wormhole',
    speed: 13,
    weight: 0,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Sprint',
    speed: 10,
    weight: 1,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'QuadCore',
    speed: 14,
    weight: 2,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'RapidCombustion',
    speed: 16,
    weight: 0,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'Accelerator',
    speed: 9,
    weight: 1,
    terrainGround:true,
     terrainWater:false,
      terrainAir: true,
  },
];

const courseOptions: course[] = [
  {
    name: 'Desert',
    length:600,
    terrainGround: true,
    terrainWater: false,
    terrainAir: false,
  },
  {
    name: 'Ocean',
    length: 600,
    terrainGround: false,
    terrainWater: true,
    terrainAir: false,
  },
  {
    name: 'Cloud-9',
    length: 600,
    terrainGround: false,
    terrainWater: false,
    terrainAir: true,
  },
]

const myCarGroundTerrain = computed(() =>
{
  let myCarAbleGround = false
  if (myChoiceBody.value.terrainGround || myChoiceWheels.value.terrainGround  ) {
    myCarAbleGround =  true
  } else {
    myCarAbleGround= false
  } return myCarAbleGround
})
const myCarWaterTerrain = computed(() =>
{
  let myCarAbleWater = false
  if (myChoiceBody.value.terrainWater || myChoiceWheels.value.terrainWater  ) {
    myCarAbleWater =  true
  } else {
    myCarAbleWater = false
  } return myCarAbleWater
})
const myCarAirTerrain = computed(() =>
{
  let myCarAbleAir = false
  if (myChoiceBody.value.terrainAir || myChoiceWheels.value.terrainAir  ) {
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
   if ( myChoiceEngine.value?.name === undefined || myChoiceWheels.value?.name === undefined || myChoiceBody.value?.name === undefined  ) {
     alert('car incomplete')
   } else if(myChoiceBody.value.name === "Boulder") {
     alert(' Its a Boulder THEY DONT MOVE')
   } else if (myChoiceCourse.value.name === undefined){
     alert ('no course selected')
   } else if (myCourseWater.value === false ){
     alert('car canot drive on this terrain')
   } else if (myChoiceWheels.value.name === "Spike Balls") {
     prompt(' You won buy popping the opponents wheels :D : enter you name so we can add you to Pro the leaderboard')}else{
     prompt(' You won :D : enter you name so we can add you to the leaderboard')
   } 
}
</script>

<template>

<center>
<h1> Car Customizer</h1>
  <br><br>
 
  <select v-model="myChoiceBody">
    <option disabled hidden value="">select body</option>
    <option v-for="body in bodyOptions" :key="body.name" :value="body">
      {{ body.name }}
    </option>
  </select>
   |
   <select v-model="myChoiceEngine">
    <option disabled hidden value="">select engine</option>
    <option v-for="engine in engineOptions" :key="engine.name" :value="engine">
      {{ engine.name }}
    </option>
  </select>
  |
  <select v-model="myChoiceWheels">
    <option disabled hidden value="">select wheel</option>
    <option v-for="Wheels in wheelOptions" :key="Wheels.name" :value="Wheels">
      {{ Wheels.name }}
    </option>
  </select> 
    <br><br>
  <p>
    Car speed:
    <span v-if= "myCarSpeed">{{ myCarSpeed }}</span>
  </p>
  <p>Car weight: {{ myWheelsType }}</p>
  <p><hr /><h2>Car Terrain</h2><hr/>ground: {{ myCarGroundTerrain }}
  <br>Water:{{ myCarWaterTerrain }}
 <br>Air:{{  myCarAirTerrain}}</p>
  
  <h2>Race courses</h2>
  <hr>
  - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
     
  <hr>
    <select  v-model = "myChoiceCourse">
    <option disabled hidden value=''>select race course</option>
    <option v-for="course in courseOptions" :key="course.name" :value="course">
      {{ course.name }}
    </option>
    </select>

    <button @click= "myCarComplete()"> race</button>
    </center>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
