<template>
  <div class="container" v-for="product in products" :key="product.id">
    <div class="item" :class="{ disabledClass: product.remainingAmount === 0 }">
      <div class="item-top">
        <h4>{{ product.name }}</h4>
        <p class="pledge">Pledge ${{ product.minPledge }} or more</p>
      </div>
      <p class="description">{{ product.description }}</p>
      <div class="item-bottom">
        <h6 class="remaining">{{ product.remainingAmount }}</h6>
        <button v-show="product.remainingAmount > 0" class="reward-btn" @click="isChecked = product.id">
          Select Reward
        </button>
        <button v-show="product.remainingAmount === 0" class="nostock-btn">
          Out of stock
        </button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      products: [
        {
          id: 1,
          name: "Bamboo Stand",
          minPledge: 25,
          description: `You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you'll still be added to the special Backer list.`,
          remainingAmount: 101,
        },
        {
          id: 2,
          name: "Black Edition Stand",
          minPledge: 75,
          description: `You get a Black Special Edition computer stand and a personal thank you. You'll be added to our Backer member list. Shipping is included.`,
          remainingAmount: 64,
        },
        {
          id: 3,
          name: "Mahogany Special Edition",
          minPledge: 200,
          description: `You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You'll be added to our Backer member list. Shipping is included.`,
          remainingAmount: 0,
        },
      ],
    };
  },
};
</script>
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  row-gap: 2rem;
}
.item {
  border: 2px solid rgb(228, 228, 228);
  padding: 2rem;
  border-radius: 12px;
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
}
.disabledClass {
  opacity: 0.4;
}
.item-top{
  display: flex;
   width: 100%;
  justify-content: space-between;
  align-items: center;
}
.item-bottom{
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
margin-top: .5rem;
}
.remaining {
  font-size: 2rem;
}
.remaining::after {
  content: "left";
  font-size: 1rem;
  font-weight: 400;
  vertical-align: top;
  line-height: 2.7rem;
  margin-left: 0.4rem;
  color: rgb(94, 94, 94);
}
.reward-btn {
  background: var(--moderatecyan);
  cursor: pointer;
  transition: .2s ease-in-out all;
}
.reward-btn:hover{
  background:var(--darkcyan);
}
.nostock-btn {
  background: var(--darkgray);
  cursor: not-allowed;
}
button {
  color: white;
  border: none;
  outline: none;
  border-radius: 50px;
  font-size: 1rem;
  font-weight: 500;
  padding-inline: 1.8rem;
  padding-block: 0.8rem;
  width: fit-content;
  height: fit-content;
}
h4{
  font-size: 1.2rem;
}
.pledge{
  color: var(--moderatecyan);
  font-weight: 400;
}
.description{
  color: rgb(94, 94, 94);
}
</style>
