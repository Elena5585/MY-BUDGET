<template>
      <div class="profititem" :id="profit.id">            
            <div class="profit__head">                  
                  <div class="profit__main">
                        <p class="profit__name" >{{ profit.title }}</p>
                        <p class="profit__amount">=  {{ profit.amount }}$</p>
                  </div >
                  <div class="profit__btns">                        
                        <button class="prof__btn"  @click="$emit('remove', profit)" id="profDelete">Delete</button>
                  </div>
            </div >
            <div class="profit__date">{{ profit.date }}</div>
      </div>
</template>

<script>
      export default {
            name: 'Profititem',
            props: {
                  profits: {
                        type: Array,
                        default: [],
                        required: true,
                  },
                  profit: {
                        type: Object,
                        default: {},
                        required: true,
                  },
                  key: {
                        type: String,
                        default: '',
                        required: true,
                  },
            }
      }
</script>

<style scoped>
      .profititem{align-self: flex-start; padding: 20px; border: 4px solid grey; border-radius: 10px; width: 100%;
      display: flex;flex-direction: column; align-items: start; justify-content: start; row-gap: 10px; color: rgb(58, 91, 58);}
      .profit__head{display: flex; flex-direction: row; justify-content: space-between; align-items: center; width: 100%;}
      .profit__btns{display: flex;flex-direction: row; justify-content: start; align-items: start; column-gap: 10px;}
      .prof__btn{width: 70px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(89, 137, 89); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
      .profit__main{display: flex; flex-direction: row; justify-content: start; align-items: start; column-gap: 8px; font-size: 1.1rem;
      font-weight: 600; }
      .profit__date{font-weight: 500; color:rgb(73, 72, 72);}
      p{margin: 0;}
</style>