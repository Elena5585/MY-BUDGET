<template>
      <div class="loseitem" :id="lose.id">            
            <div class="lose__head">
                  <div class="lose__main">
                        <p class="lose__name">{{ lose.title }}</p>
                                               
                        <p class="lose__amount">=  {{ lose.amount }}$</p>
                  </div >
                  <div class="loses__btns">                        
                        <button class="lose__btn" @click="$emit('remove', lose)" id="loseDelete">Delete</button>
                  </div>
            </div >
            <p class="lose__category">{{ lose.category }}</p> 
            <div class="lose__date">{{ lose.date }}</div>
      </div>
</template>

<script>
      export default {
            name: 'Loseitem',
            props: {
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
                  key: {
                        type: String,
                        default: '',
                        required: true,
                  },
            }
      }
</script>

<style scoped>
      .loseitem{align-self: flex-start; padding: 20px; border: 4px solid grey; border-radius: 10px; width: 100%;
      display: flex;flex-direction: column; align-items: start; justify-content: start; row-gap: 10px; color: rgb(58, 91, 58);}
      .lose__head{display: flex; flex-direction: row; justify-content: space-between; align-items: center; width: 100%;}
      .loses__btns{display: flex;flex-direction: row; justify-content: start; align-items: start; column-gap: 10px;}
      .lose__btn{width: 70px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(194, 91, 120); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}

      .lose__main{display: flex; flex-direction: row; justify-content: start; align-items: start; column-gap: 8px; font-size: 1.1rem;
      font-weight: 600; }
      .lose__date{font-weight: 500; color:rgb(73, 72, 72);}
      .lose__category{color:rgb(73, 72, 72);}
      p{margin: 0;}
</style>