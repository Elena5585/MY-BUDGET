<template>
      <form class="add__profit" @submit.prevent="addProfit">
            <input type="text" placeholder="Profit:" v-model="title" class="add__profit-input">
            <input type="text" placeholder="Amount:" v-model.number="amount" class="add__profit-input">            
            <button class="prof__btn" id="profAdd">Add new profit</button>
      </form>
</template>

<script>
      export default {
            name: 'AddFormProfit',
            data(){
                  return{
                        title: '',
                        amount: 0,
                  }
            },
            methods: {
                  addProfit() {
                        const obj = {
                              title: this.title,
                              amount: this.amount,
                              date: new Date().toLocaleDateString(),
                              id: Date.now(),
                        };
                        this.$emit("add-profit", obj);                        
                        this.title = '';
                        this.amount= '';
                  },
            },
      }
</script>

<style scoped>
      .add__profit{ display: flex; flex-direction: column; row-gap: 15px; margin-top: 15px; border-radius: 20px;
       border: 5px solid rgb(89, 137, 89);  padding: 20px; width: 85%;
      }
      .add__profit-input{outline: none; border-radius: 10px; border: 2px solid rgb(89, 137, 89); font-size: 1.1rem; font-weight: 500;
       padding: 5px; text-align: center; color:rgb(85, 84, 84);}
      .prof__btn{width: 200px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(89, 137, 89); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
</style>