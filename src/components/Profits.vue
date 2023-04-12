<template>
      <div class="profit__unit">
            <h2 class="profits__title">PROFITS ARTICLES:</h2>
            <div class="profits">
                  <Profititem 
                  v-for="(profit, key) in profits" 
                  :profit="profit" 
                  :key="key"
                  @remove="$emit('remove', profit)"
                  ></Profititem>
            </div>
            <div class="total__profits">TOTAL PROFIT AMOUNT = {{ totalProfits }} $</div>
      </div >
</template>

<script>
import Profititem from './Profititem.vue';

      export default {
            name: 'Profits',
            components: {
                  Profititem,
            },
            props: {
                  profits: {
                        type: Array,
                        default: [],
                        required: true,
                  },
                  totalProfits:{
                        type: String,
                        default: '',
                        required: true,
                  }
            }
      }
</script>

<style scoped>
      .profit__unit{display: flex; flex-direction: column; justify-content: start;; align-items: start; row-gap: 20px; box-shadow: 0 0 10px 5px grey;
      border-radius: 25px; padding: 25px; font-size: 1.1rem; font-weight: 500; flex-basis: 45%;}
      .profits__title{font-size: 1.4rem; font-weight: 600; color: rgb(43, 79, 43);}
      .profits{display: flex; flex-direction: column; justify-content: start; align-items: start; row-gap: 20px; margin: 0;
       padding: 0; width: 90%;}
       .total__profits{ padding: 20px; box-shadow: 5px 5px 5px 3px rgb(85, 84, 84); border-radius: 10px; width: 90%; font-size: 1.3rem;
       font-weight: 500;background-color: rgb(89, 137, 89); color:rgb(219, 215, 215); }
</style>