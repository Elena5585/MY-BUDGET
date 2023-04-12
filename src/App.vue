<template>
    <div class="trackers">
          <h1 class="app__title">
            MY BALANCE
            <span>&#128176;</span>
            <p id="balance__tracker">{{ balance }}$</p>
         </h1>

         <Trackers         
         :maxProf="maxProf" 
         :maxExp="maxExp" 
         :maxProfTitle="maxProfTitle"
         :maxExpTitle="maxExpTitle" 
         :maxCategory="maxCategory"
         :food="food" 
         :appliance="appliance"
         :travel="travel"
         :medicine="medicine"
         :pet="pet"
         :shopping="shopping"
         :car="car"
         :loses="loses"
         @show-maxprofit="showMaxProfit"
         @show-maxexpence="showMaxExp"
         @show-category="showMaxCategory"
         ></Trackers>

         <AddFormProfit         
         @add-profit="toTotalProfits"
         ></AddFormProfit>

         <AddFormLose
         @add-lose="toTotalLoses"         
         ></AddFormLose>
    </div>
   
    <div class="articles">
          <Profits
          :profits="profits"
          :totalProfits="totalProfits"
          @remove="removeProfit"
          ></Profits>

          <Loses
          :loses="loses"
          :totalLoses="totalLoses"
          @remove="removeLose"
          ></Loses> 
    </div>
    
</template>

<script>
import Profits from './components/Profits.vue';
import Loses from './components/Loses.vue';
import Trackers from './components/Trackers.vue';
import AddFormProfit from'./components/AddFormProfit.vue';
import AddFormLose from './components/AddFormLose.vue';

export default {
      name: 'App',
      components: {
            Profits,
            Loses,
            Trackers,
            AddFormProfit,
            AddFormLose,
            
      },
      data(){
            return{
                  balance: 0,
                  maxProf: 0,
                  maxExp: 0,
                  profits: [
                        {title: 'Salary', amount: 2000, date: new Date().toLocaleDateString(), id: 1,},
                        {title: 'Website profit', amount: 500, date: new Date().toLocaleDateString(), id: 2,},
                        {title: 'Shop profit', amount: 1500, date: new Date().toLocaleDateString(), id: 3,},
                  ],
                  loses: [
                        {title: 'Food products', amount: 1900, date: new Date().toLocaleDateString(), id: 1, category: 'Food products'},
                        {title: 'Shopping', amount: 400, date: new Date().toLocaleDateString(), id: 2, category: 'Shopping'},
                        {title: 'Cat feed', amount: 80, date: new Date().toLocaleDateString(), id: 3, category: 'Pet care'},
                        {title: 'Trip to Bali', amount: 1200, date: new Date().toLocaleDateString(), id: 4, category: 'Travelling'},
                        {title: 'Medicines', amount: 65, date: new Date().toLocaleDateString(), id: 5, category: 'Medical service and medicines'},

                  ],
                  totalProfits: 0,
                  totalLoses: 0,
                  maxProfTitle: '',
                  maxExpTitle: '',
                  food: 0,
                  foodName: '',
                  appliance: 0,
                  applianceName: '',
                  travel: 0,
                  travelName: '',
                  medicine: 0,
                  medicineName: '',
                  pet: 0,
                  petName: '',
                  shopping: 0,
                  shoppingName: '',
                  car: 0,
                  carName: '',
                  maxCategory: '',
                  maxCategoryName: '',
                  

            }
      },
      mounted(){ 
            this.toTotalProfit(),
            this.toTotalLose(),
            this.toBalance(),
            this.tomaxProfit(),
            this.tomaxExpense(),
            this.showCategories()           
      },
      methods:{ 
            showMaxCategory() {
                  if(this.food === this.maxCategory){                        
                        this.maxCategoryName = this.foodName;                        
                        document.querySelector('#food').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#food').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#food').style.backgroundColor = 'transparent';
                              document.querySelector('#food').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                  if(this.appliance === this.maxCategory){
                        this.maxCategoryName = this.applianceName;                        
                        document.querySelector('#home').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#home').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#home').style.backgroundColor = 'transparent';
                              document.querySelector('#home').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                  if(this.medicine === this.maxCategory){
                        this.maxCategoryName = this.medicineName;                        
                        document.querySelector('#medicine').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#medicine').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#medicine').style.backgroundColor = 'transparent';
                              document.querySelector('#medicine').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                  if(this.travel === this.maxCategory){
                        this.maxCategoryName = this.travelName;                        
                        document.querySelector('#travel').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#travel').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#travel').style.backgroundColor = 'transparent';
                              document.querySelector('#travel').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                  if(this.shopping === this.maxCategory){
                        this.maxCategoryName = this.shoppingName;                        
                        document.querySelector('#shopping').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#shopping').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#shopping').style.backgroundColor = 'transparent';
                              document.querySelector('#shopping').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                  if(this.pet === this.maxCategory){
                        this.maxCategoryName = this.petName;                        
                        document.querySelector('#pet').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#pet').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#pet').style.backgroundColor = 'transparent';
                              document.querySelector('#pet').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                  if(this.car === this.maxCategory){
                        this.maxCategoryName = this.carName;                        
                        document.querySelector('#car').style.backgroundColor = 'rgb(194, 91, 120)';
                        document.querySelector('#car').style.color = 'rgb(219, 215, 215)';
                        setTimeout(() => {
                              document.querySelector('#car').style.backgroundColor = 'transparent';
                              document.querySelector('#car').style.color = 'rgb(74, 73, 73)';
                        }, 4000)
                 }
                 
            },          
            showMaxExp(){
                  this.maxExp = Math.max(...this.loses.map(obj => obj.amount));                               
                  for(let i = 0; i < this.loses.length; i++){                      
                        if(this.maxExp === this.loses[i].amount){
                              this.maxExpTitle = this.loses[i].title;                              
                              const loseitems = [...document.querySelectorAll('.loseitem')];  
                              for(let j= 0; j< loseitems.length; j++){                              
                                    if(j === i){                                    
                                          loseitems[j].style.backgroundColor = 'rgb(194, 91, 120)';
                                          loseitems[j].style.color = 'rgb(219, 215, 215)';
                                          const catblocks = [...document.querySelectorAll('.lose__category')];
                                          catblocks[j].style.color = 'rgb(219, 215, 215)';
                                          const dateblocks = [...document.querySelectorAll('.lose__date')];
                                          dateblocks[j].style.color = 'rgb(219, 215, 215)';
                                          setTimeout(() => {
                                          loseitems[j].style.backgroundColor = 'transparent';
                                          loseitems[j].style.color = 'rgb(73, 72, 72)';
                                          const catblocks = [...document.querySelectorAll('.lose__category')];
                                          catblocks[j].style.color = 'rgb(73, 72, 72)';
                                          const dateblocks = [...document.querySelectorAll('.lose__date')];
                                          dateblocks[j].style.color = 'rgb(73, 72, 72)';
                                          }, 4000)
                        }}}} 
            },  
            showMaxProfit(){
                  this.maxProf = Math.max(...this.profits.map(obj => obj.amount));
                  for(let i = 0; i < this.profits.length; i++){                        
                        if(this.maxProf === this.profits[i].amount){
                              this.maxProfTitle = this.profits[i].title;
                              const profititems = [...document.querySelectorAll('.profititem')];                             
                              for(let j= 0; j< profititems.length; j++){                              
                                    if(j === i){                                    
                                          profititems[j].style.backgroundColor = 'rgb(89, 137, 89)';
                                          profititems[j].style.color = 'rgb(219, 215, 215)';
                                          const dateblocks = [...document.querySelectorAll('.profit__date')];
                                          dateblocks[j].style.color = 'rgb(219, 215, 215)';
                                          setTimeout(() => {
                                                profititems[j].style.backgroundColor = 'transparent';
                                                profititems[j].style.color = 'rgb(58, 91, 58)';
                                                const dateblocks = [...document.querySelectorAll('.profit__date')];
                                                dateblocks[j].style.color = 'rgb(73, 72, 72)';
                                          }, 4000)
                                    }                              
                              }                              
                        }
                  }  

            },          
            removeProfit(profit){
                  this.profits = this.profits.filter((elem) => {
                        return elem.id !== profit.id;
                  });
                  this.totalProfits = 0;               
                  for(let i = 0; i < this.profits.length; i++){
                        this.totalProfits += this.profits[i].amount;                       
                  }                 
                  this.balance = this.totalProfits - this.totalLoses; 
                  if(this.balance < 0)  {
                        document.querySelector('#balance__tracker').style.color = 'red';
                  }else {
                        document.querySelector('#balance__tracker').style.color = 'rgb(89, 137, 89)'; 
                  } 

                  this.maxProf = Math.max(...this.profits.map(obj => obj.amount));
                  for(let i = 0; i < this.profits.length; i++){                        
                        if(this.maxProf === this.profits[i].amount){
                              this.maxProfTitle = this.profits[i].title;
                        }
                  } 
            },   
            clear()  {
                  this.food = 0;
                  this.appliance = 0;
                  this.medicine = 0;
                  this.pet = 0;
                  this.shopping= 0;
                  this.car= 0;
                  this.travel= 0;
            },      
            removeLose(lose){
                  this.loses = this.loses.filter((elem) => {
                        return elem.id !== lose.id;
                  });
                  this.totalLoses = 0;                                                               
                  for(let i = 0; i < this.loses.length; i++){
                        this.totalLoses += this.loses[i].amount;                  
                  }                     
                  this.balance = this.totalProfits - this.totalLoses;
                  if(this.balance < 0)  {
                        document.querySelector('#balance__tracker').style.color = 'red';
                  }else {
                        document.querySelector('#balance__tracker').style.color = 'rgb(89, 137, 89)'; 
                  }  

                  this.maxExp = Math.max(...this.loses.map(obj => obj.amount));                
                  for(let i = 0; i < this.loses.length; i++){                      
                        if(this.maxExp === this.loses[i].amount){
                              this.maxExpTitle = this.loses[i].title;                              
                        }
                  } 
                  
                  this.clear()

                  this.loses.forEach(lose => {
                   switch(lose.category){
                        case 'Food products': this.food += lose.amount; break;
                        case 'Home appliances': this.appliance += lose.amount; break;                        
                        case 'Medical service and medicines': this.medicine += lose.amount; break;
                        case 'Pet care': this.pet += lose.amount; break;
                        case 'Shopping': this.shopping += lose.amount; break;
                        case 'Car service': this.car+= lose.amount; break;
                        case 'Travelling': this.travel+= lose.amount; break;                                           }
                 })
                 this.maxCategory = Math.max(this.food, this.appliance, this.medicine, this.travel, this.car, this.pet, this.shopping) 
            }, 
            toTotalProfits(obj){                                    
                  this.profits.push(obj);                  
                  this.totalProfits = 0;               
                  for(let i = 0; i < this.profits.length; i++){
                        this.totalProfits += this.profits[i].amount;                       
                  }  

                  this.balance = this.totalProfits - this.totalLoses;
                  if(this.balance < 0)  {
                        document.querySelector('#balance__tracker').style.color = 'red';
                  }else {
                        document.querySelector('#balance__tracker').style.color = 'rgb(89, 137, 89)'; 
                  } 

                  this.maxProf = Math.max(...this.profits.map(obj => obj.amount));
                  for(let i = 0; i < this.profits.length; i++){                        
                        if(this.maxProf === this.profits[i].amount){
                              this.maxProfTitle = this.profits[i].title;
                        }
                  }                                                            
            }, 

            toTotalLoses(object){ 
                  this.loses.push(object); 
                  this.totalLoses = 0;                                                               
                  for(let i = 0; i < this.loses.length; i++){
                        this.totalLoses += this.loses[i].amount;                  
                  }                     
                  this.balance = this.totalProfits - this.totalLoses;
                  if(this.balance < 0)  {
                        document.querySelector('#balance__tracker').style.color = 'red';
                  }else {
                        document.querySelector('#balance__tracker').style.color = 'rgb(89, 137, 89)'; 
                  } 

                  this.maxExp = Math.max(...this.loses.map(obj => obj.amount));                
                  for(let i = 0; i < this.loses.length; i++){                      
                        if(this.maxExp === this.loses[i].amount){
                              this.maxExpTitle = this.loses[i].title;                              
                        }
                  } 

                  this.clear();

                  this.loses.forEach(lose => {
                        console.log(lose.category);
                   switch(lose.category){
                        case 'Food products': this.food += lose.amount; break;
                        case 'Home appliances': this.appliance += lose.amount; break;                        
                        case 'Medical service and medicines': this.medicine += lose.amount; break;
                        case 'Pet care': this.pet += lose.amount; break;
                        case 'Shopping': this.shopping += lose.amount; break;
                        case 'Car service': this.car += lose.amount; break;
                        case 'Travelling': this.travel += lose.amount; break;                                           }
                 }) 
                 this.maxCategory = Math.max(this.food, this.appliance, this.medicine, this.travel, this.car, this.pet, this.shopping)     
            },        
            toTotalProfit(){                                  
                  for(let i = 0; i < this.profits.length; i++){
                  this.totalProfits += this.profits[i].amount;
                  }                                   
            },
            
            toTotalLose(){                                                                                
                  for(let i = 0; i < this.loses.length; i++){
                  this.totalLoses += this.loses[i].amount;                               
                  }                 
            },
            
            toBalance(){
                  this.balance = this.totalProfits - this.totalLoses;
                  
                  if(this.balance < 0)  {
                        document.querySelector('#balance__tracker').style.color = 'red';
                  }else {
                        document.querySelector('#balance__tracker').style.color = 'rgb(89, 137, 89)'; 
                  }                
            },            
            tomaxProfit(){                  
                  this.maxProf = Math.max(...this.profits.map(obj => obj.amount));
                  for(let i = 0; i < this.profits.length; i++){                        
                        if(this.maxProf === this.profits[i].amount){
                              this.maxProfTitle = this.profits[i].title;     
                        }
                  }                    
            },
            tomaxExpense(){   
                  this.maxExp = Math.max(...this.loses.map(obj => obj.amount));                
                  for(let i = 0; i < this.loses.length; i++){                      
                        if(this.maxExp === this.loses[i].amount){
                              this.maxExpTitle = this.loses[i].title;                              
                        }
                  }                                 
            },  
            showCategories(){
                 this.loses.forEach(lose => {
                   switch(lose.category){
                        case 'Food products': {
                               this.food += lose.amount; 
                               this.foodName = 'Food products';
                               break;
                              }
                        case 'Home appliances': {
                              this.appliance += lose.amount;
                              this.applianceName = 'Home appliances';
                              break;}                        
                        case 'Medical service and medicines': {
                              this.medicine += lose.amount;
                              this.medicineName = 'Medical service and medicines';
                              break;
                        }
                        case 'Pet care': {
                              this.pet += lose.amount;
                              this.petName = 'Pet care';
                              break;
                        }
                        case 'Shopping': {
                              this.shopping += lose.amount;
                              this.shoppingName = 'Shopping'; 
                              break;
                        }
                        case 'Car service': {
                              this.car += lose.amount;
                              this.carName = 'Car service';
                              break;
                        }
                        case 'Travelling': {
                              this.travel += lose.amount;
                              this.travelName = 'Travelling';
                              break; 
                        }
                  }
                 })                 
                 this.maxCategory = Math.max(this.food, this.appliance, this.medicine, this.travel, this.car, this.pet, this.shopping)              
           
            },      
            
      }

}
</script>

<style>

body{padding: 25px; background: linear-gradient(90deg, rgb(231, 231, 180),rgb(226, 218, 212), rgb(248, 236, 168));}
#app {font-family: Avenir, Helvetica, Arial, sans-serif;  -webkit-font-smoothing: antialiased;  -moz-osx-font-smoothing: grayscale;
display: flex; flex-direction: row; justify-content: start; align-items: start; column-gap: 50px;}
.trackers{flex-basis: 35%; display: flex; flex-direction: column; justify-content: start; align-items: start; row-gap: 20px; font-size: 1.3rem;}
.app__title{ border-radius: 20px; padding: 20px; box-shadow: 0 0 20px 3px rgb(73, 72, 72); color: rgb(80, 79, 79); 
margin-right: 10px; font-size: 1.4rem;}
span{font-size: 2rem;}
#balance__tracker{text-align: center;}
.balance__remain{font-size: 1.2rem; font-weight: 600; padding-left: 15px; color: rgb(109, 109, 109);}
.articles{display: flex; flex-direction: row; justify-content: start; align-items: start; column-gap: 40px; flex-basis: 65%;}
</style>
