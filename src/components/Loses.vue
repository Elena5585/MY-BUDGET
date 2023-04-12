<template>
      <div class="lose__unit">
            <h2 class="loses__title">EXPENCES ARTICLES:</h2>
            <div class="loses">
                  <Loseitem
                  v-for="(lose, key) in loses"
                  :lose="lose"
                  :key="key"
                  @remove="$emit('remove', lose)"
                  ></Loseitem>
            </div>
            <div class="total__loses">TOTAL EXPENCES AMOUNT = {{ totalLoses }} $</div>
      </div >
</template>

<script>
import Loseitem from './Loseitem.vue';

export default {
      name: "Loses",
      components: {
            Loseitem,
      },
      components: { Loseitem },
      props: {
            loses: {
                  type: Array,
                  default: [],
                  required: true,
            },
            totalLoses:{
                  type: Number,                  
                  required: true,
            }
      },

}
</script>

<style scoped>
      .lose__unit{display: flex; flex-direction: column; justify-content: start;; align-items: start; row-gap: 20px; box-shadow: 0 0 10px 5px grey;
      border-radius: 25px; padding: 25px; font-size: 1.1rem; font-weight: 500; flex-basis: 45%;}
      .loses__title{font-size: 1.4rem; font-weight: 600; color: rgb(43, 79, 43);}
      .loses{display: flex; flex-direction: column; justify-content: start; align-items: start; row-gap: 20px; margin: 0;
       padding: 0; width: 90%;}
       .total__loses{ padding: 20px; box-shadow: 5px 5px 5px 3px rgb(85, 84, 84); border-radius: 10px; width: 90%; font-size: 1.2rem;
      font-weight: 500; background-color: rgb(194, 91, 120); color:rgb(219, 215, 215); }
</style>