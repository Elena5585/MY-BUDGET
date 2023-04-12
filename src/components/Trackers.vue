<template>  
      <div class="tracker__block">
            <button class="tracker_profit" @click="$emit('show-maxprofit')">MAX PROFIT : {{ maxProf }} $ </button>
            <button class="tracker_lose" @click="$emit('show-maxexpence')">MAX EXPENSE : {{ maxExp }} $ </button>
            <button class="tracker_maxcategory" @click="$emit('show-category')">MAX CATEGORY : {{ maxCategory }} $ </button>
            <button class="tracker_category" id="food">FOOD CATEGORY : {{ food }} $ </button>
            <button class="tracker_category" id="home">HOME APPLIANCE CATEGORY : {{ appliance }} $ </button>
            <button class="tracker_category" id="medicine">MEDICINE CATEGORY : {{ medicine }} $ </button>
            <button class="tracker_category" id="travel">TRAVEL CATEGORY : {{ travel }} $ </button>
            <button class="tracker_category" id="shopping">SHOPPING CATEGORY : {{ shopping }} $ </button>
            <button class="tracker_category" id="pet">PET CARE CATEGORY : {{ pet }} $ </button>
            <button class="tracker_category" id="car">CAR SERVICE CATEGORY : {{ car }} $ </button>
            
      </div>           
      
      
</template>

<script>
      export default {
            name: 'Trackers',
            props:{
                  loses: {
                        type: Array,
                        default: [],
                        required: true,
                  },
                  lose: {
                        type: Object,
                        default: {},
                        required: true,
                  },                  
                  food: {
                        type: Number,                        
                        required: true,
                  },
                  shopping: {
                        type: Number,                        
                        required: true,
                  },
                  appliance: {
                        type: Number,                        
                        required: true,
                  },
                  medicine: {
                        type: Number,                        
                        required: true,
                  },
                  travel: {
                        type: Number,                        
                        required: true,
                  },
                  pet: {
                        type: Number,                        
                        required: true,
                  },
                  car: {
                        type: Number,                        
                        required: true,
                  },
                  maxProf: {
                        type: String,
                        default: '',
                        required: true,
                  },
                  maxCategory: {
                        type: String,
                        default: '',
                        required: true,
                  },
                  maxExp: {
                        type: String,
                        default: '',
                        required: true,
                  },
                  maxProfTitle:{
                        type: String,
                        default: '',
                        required: true,
                  },
                  maxExpTitle:{
                        type: String,
                        default: '',
                        required: true,
                  },
            }
      }
</script>

<style scoped>
      #profMaxTitle{color: rgb(89, 137, 89); text-transform: uppercase; font-size: 1.2rem;}
      #expMaxTitle{color: rgb(194, 91, 120); text-transform: uppercase; font-size: 1.2rem;}
      p{margin: 0;}
      .tracker__block{display: flex; flex-direction: row; gap: 20px; flex-wrap: wrap;}
      .tracker_profit{width: 230px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(89, 137, 89); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
      .tracker_lose{width: 230px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(194, 91, 120); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
      .tracker_maxcategory{width: 230px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(53, 125, 151); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
      .tracker_category{width: 230px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 0.8rem; font-weight: 500;
      padding: 5px; background-color: transparent; color:rgb(74, 73, 73); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
      .balance__category{margin-top: 20px; color: rgb(194, 91, 120); font-weight: 600; font-size: 1.4rem;}
      .balance__remain{font-size: 1.1rem;}
      
</style>