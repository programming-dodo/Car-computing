<script setup lang="ts">
import { ref, computed } from 'vue';

const myChoiceWheels = ref('');
const myChoiceBody = ref('');
const myChoiceEngine = ref('');
const myChoiceCourse = ref ('');

interface carType {
  speed: number;
  weight: number;
  terrainground: boolean;
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
  terrainground: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
}
interface bodyOptions {
  name: string;
  speed: number;
  weight: number;
  terrainground: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
  
}

interface engineOptions {
  name: string;
  speed: number;
  weight: number;
  terrainground: boolean;
  terrainWater: boolean;
  terrainAir: boolean;
}

interface courseOptions {
  name: string;
  length: number;
  terrainground: boolean;
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
    terrainground: false,
     terrainWater: false,
      terrainAir: true,
  },
  {
    name: 'grippers',
    speed: 9,
    weight: 1,
    terrainground: true,
     terrainWater: false,
      terrainAir: false,
  },
  {
    name: 'paddle wheels',
    speed: 4,
    weight: 2,
    terrainground:false,
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
    terrainground:false,
     terrainWater:true,
      terrainAir: true,
  },
  {
    name: 'dodomobile',
    speed: 10,
    weight: 1,
    terrainground:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'Boulder',
    speed: -40,
    weight: 20,
    terrainground:true,
     terrainWater:false,
      terrainAir: false,
    
  },
];

const engine = [];

const engineOptions: enigne[] = [
  {
    name: 'cheetah',
    speed: 15,
    weight: 0,
    terrainground:true,
     terrainWater:false,
      terrainAir: false,
  },
  {
    name: 'lockness',
    speed: 10,
    weight: 1,
    terrainground:false,
     terrainWater:false,
      terrainAir: true,
  },
  {
    name: 'dragonFueled',
    speed: 12,
    weight: 2,
    terrainground:true,
     terrainWater:false,
      terrainAir: true,
  },
];

const courseOptions: course[] = [
  {
    name: 'desert',
    length:600,
    terrainground: true ,
    terrainWater: false,
    terrainAir: false,
  },
  {
    name: 'ocean',
    length: 600,
    terrainground: false,
    terrainWater: true,
    terrainAir: false,
  },
  {
    name: 'clouds',
    length: 600,
    terrainground: false,
    terrainWater: false,
    terrainAir: true,
  },
]

const myCarGroundTerrain = computed(() =>
{
  if (myChoiceBody.value.terrainground === true| myChoiceWheels.value.terrainground === true ) {
    return  true
  } else {
    return false
  }
})
const myCarWaterTerrain = computed(() =>
{
  if (myChoiceBody.value.terrainWater === true| myChoiceWheels.value.terrainWater === true ) {
    return  true
  } else {
    return false
  }
})
const myCarAirTerrain = computed(() =>
{
  if (myChoiceBody.value.terrainAir === true| myChoiceWheels.value.terrainAir === true ) {
    return  true
  } else {
    return false
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

  console.log(myCarSpeed);
  return speedDisplay;
});
console.log;
const myWheelType = computed(() => {
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
  console.log(total);
  return weight;
});
</script>

<template>
  <p>
    speed:
    {{ myCarSpeed }}
  </p>
  <p>weight: {{ myWheelType }}</p>
  <p>terrain<hr/>ground: {{ myCarGroundTerrain }}
  <hr/>Water:{{ myCarWaterTerrain }}
 <hr/>Air:{{  myCarAirTerrain}}</p>
 
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
    <select v-model = "myChoiceCourse">
    <option diabled hidden value=''>select race course</option>
    <option v-for="course in courseOptions" :key="course.name" :value="course">
      {{ course.name }}
    </option>
    </select>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
