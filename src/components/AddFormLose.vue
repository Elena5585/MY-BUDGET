<template>
      <form class="add__lose" @submit.prevent="addLose">
            <input type="text" v-model="titleL" placeholder="Expense:" class="add__lose-input">
            <input type="text" v-model.number="amountL" placeholder="Amount:" class="add__lose-input">
            <select required v-model="category" placeholder="Category:" class="add__lose-input">
                  <option value="Food products">Food products</option>
                  <option value="Home appliances">Home appliances</option>
                  <option value="Medical service and medicines">Medical service and medicines</option>
                  <option value="Shopping">Shopping</option>
                  <option value="Car service">Car service</option>
                  <option value="Travelling">Travelling</option>
                  <option value="Pet care">Pet care</option>
            </select>
            <button class="lose__btn" id="loseAdd">Add new expense</button>
      </form>
</template>

<script>
      export default {
            name: 'AddFormLose',
            data(){
                  return{
                        titleL: '',
                        amountL: 0,
                        category: '',
                  }

            },
            methods: {
                  addLose() {
                        const object = {
                              title: this.titleL,
                              amount: this.amountL,
                              category: this.category,
                              date: new Date().toLocaleDateString(),
                              id: Date.now(),
                        };                        
                        this.$emit("add-lose", object);
                        this.titleL = '';
                        this.amountL= '';
                        this.category= '';
                  },
            },
      }
</script>

<style scoped>
      .add__lose{ display: flex; flex-direction: column; row-gap: 15px; margin-top: 15px; border-radius: 20px;
       border: 5px solid rgb(194, 91, 120);  padding: 20px; width: 85%;
      }
      .add__lose-input{outline: none; border-radius: 10px; border: 2px solid rgb(194, 91, 120); font-size: 1.1rem; font-weight: 500;
       padding: 5px; text-align: center; color:rgb(85, 84, 84);}
      .lose__btn{width: 200px; height: 40px; border: none; border-radius: 10px; outline: none; font-size: 1.1rem; font-weight: 500;
      padding: 5px; background-color: rgb(194, 91, 120); color:rgb(219, 215, 215); box-shadow: 5px 5px 5px 3px rgb(85, 84, 84);}
</style>