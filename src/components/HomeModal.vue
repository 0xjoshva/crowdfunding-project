<template>
    <div class="modal-backdrop">
  <div class="modal">
    <div class="modal-top">
    <h1>Back this project</h1>
    <button @click="!modalOpen">huh</button>
</div>
    <p>
      Want to support us in bringing Mastercraft Bamboo Monitor Riser out in the
      world?
    </p>
    <div class="container">
      <div class="item" @click="isChecked = !isChecked">
        <div class="circle" :class="{ checked: isChecked }"></div>
      </div>
    </div>
  </div></div>
</template>
<script>
export default {
  data() {
    return {
      products: [
        {
          id: 0,
          name: "Pledge with no reward",
          minPledge: 0,
          description: `Choose to support us without a reward if you simply believe in our project as a backer, you will be signed up to receive product updates via email.`,
          remainingAmount: "",
        },
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
.modal-backdrop{
    height: 100vh;
    position: fixed;
    width: 100%;
    background: rgba(0, 0, 0, 0.495);
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
}
.modal{
    position: absolute;
    z-index: 11;
    background: white;
}
.circle {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  border: 1px solid grey;
  background: white
}
</style>
