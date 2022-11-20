<template>
  <main>
    <section id="home">
      <div class="modal-backdrop" v-show="modalOpen">
        <div class="modal">
          <button
            @click="(modalOpen = false), (isChecked = null)"
            class="btnclose"
          >
            <img src="../assets/icon-close-modal.svg" alt="" />
          </button>
          <div class="heading">
            <h1>Back this project</h1>

            <p>
              Want to support us in bringing Mastercraft Bamboo Monitor Riser
              out in the world?
            </p>
          </div>
          <div class="modal-container">
            <button
              class="modal-item"
              @click="isChecked = product.id"
              v-for="product in products"
              :key="product.id"
              :disabled="product.remainingAmount === 0"
              :class="{
                disabled: product.remainingAmount === 0,
                modalItemChecked: isChecked === product.id,
              }"
              @mouseenter="hover = product.id"
              @mouseleave="hover = null"
            >
              <div class="row">
                <div
                  class="circle"
                  :class="{
                    hovered: hover === product.id && isChecked === null,
                  }"
                >
                  <div class="center" v-if="isChecked === product.id"></div>
                  <div v-else-if="product.remainingAmount === 0"></div>
                </div>
                <div class="content">
                  <div class="content-top">
                    <div class="first">
                      <div
                        class="title"
                        :class="{
                          texthover: hover === product.id && isChecked === null,
                        }"
                      >
                        {{ product.name }}
                      </div>
                      <div class="pledge" v-if="product.minPledge > 0">
                        Pledge ${{ product.minPledge }} or more
                      </div>
                    </div>
                    <div class="amount">
                      {{ product.remainingAmount }}
                      <span v-show="product.id > 0">left</span>
                    </div>
                  </div>
                  <div class="description">{{ product.description }}</div>
                </div>
              </div>
              <div class="input-div" v-if="isChecked === product.id">
                <p>Enter your pledge</p>
                <div class="end">
                  <label for="minpledge"
                    ><p>$</p>
                    <input
                      type="text"
                      :value="product.minPledge"
                      name="minpledge"
                  /></label>
                  <button
                    @click="(modalOpen = false), (thankYouModalOpen = true)"
                  >
                    Continue
                  </button>
                </div>
              </div>
            </button>
          </div>
        </div>
      </div>
      <div class="modal-backdrop" v-show="thankYouModalOpen">
        <div class="thankyou-modal">
          <img src="../assets/icon-check.svg" alt="">
          <h2>Thanks for your support!</h2>
          <p>Your pledge brings us one step closer to sharing Mastercraft Bamboo Monitor Riser worldwide. You will get an email once our campaign in completed.</p>
          <button @click="thankYouModalOpen = false">Got it!</button>
        </div>
      </div>
      <nav>
        <img src="../assets/logo.svg" alt="" />
        <div class="links">
          <a href="">About</a>
          <a href="">Discover</a>
          <a href="">Get Started</a>
        </div>
      </nav>
    </section>
    <section id="crowdfund">
      <div class="panel-div">
        <div class="top panel">
          <img
            src="../assets/logo-mastercraft.svg"
            alt=""
            class="mastercraft-logo"
          />
          <h1>Mastercraft Bamboo Monitor Riser</h1>
          <p>
            A beautiful & handcrafted monitor stand to reduce neck and eye
            strain.
          </p>
          <div class="btn-group">
            <button class="back-btn" @click="modalOpen = true">
              Back this project
            </button>
            <button
              class="bookmark-btn"
              :class="{ checked: bookMarked }"
              @click="bookMarked = !bookMarked"
            >
              <img src="../assets/icon-bookmark.svg" alt="" />
              <p>Bookmark<span v-show="bookMarked">ed</span></p>
            </button>
          </div>
        </div>
        <div class="mid panel">
          <div class="mid-values">
            <div class="mid-values-item">
              <h2>$89,914</h2>
              <p>of $100,000 backed</p>
            </div>
            <div class="mid-values-item">
              <h2>5,007</h2>
              <p>total backers</p>
            </div>
            <div class="mid-values-item">
              <h2>56</h2>
              <p>days left</p>
            </div>
            <!-- slider -->
          </div>
          <div class="bar">
            <div class="progress"></div>
          </div>
        </div>
        <div class="bottom panel">
          <h6>About this project</h6>
          <div class="para">
            <p>
              The Mastercraft Bamboo Monitor Riser is a sturdy and stylish
              platform that elevates your screen to a more comfortable viewing
              height. Placing your monitor at eye level has the potential to
              improve your posture and make you more comfortable while at work,
              helping you stay focused on the task at hand.
            </p>
            <p>
              Featuring artisan craftmanship, the simplicity of design creates
              extra desk space below your computer to allow notepads, pens, and
              USB sticks to be stores under the stand.
            </p>
          </div>
          <div
            class="container"
            v-for="product in products"
            :key="product.id"
            v-show="product.id > 0"
          >
            <div
              class="item"
              :class="{ disabledClass: product.remainingAmount === 0 }"
            >
              <div class="item-top">
                <h4>{{ product.name }}</h4>
                <p class="pledge">Pledge ${{ product.minPledge }} or more</p>
              </div>
              <p class="description">{{ product.description }}</p>
              <div class="item-bottom">
                <h6 class="remaining">
                  {{ product.remainingAmount }}<span>left</span>
                </h6>
                <button
                  v-show="product.remainingAmount > 0"
                  class="reward-btn"
                  @click="(isChecked = product.id), (modalOpen = true)"
                >
                  Select Reward
                </button>
                <button
                  v-show="product.remainingAmount === 0"
                  class="nostock-btn"
                >
                  Out of stock
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import BottomItems from "@/components/BottomItems.vue";
import Modal from "@/components/HomeModal.vue";
export default {
  data() {
    return {
      products: [
        {
          id: 0,
          name: "Pledge with no reward",
          minPledge: 0,
          description: `Choose to support us without a reward if you simply believe in our project as a backer, you will be signed up to receive product updates via email.`,
          remainingAmount: null,
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
      bookMarked: false,
      modalOpen: false,
      isChecked: null,
      thankYouModalOpen: true,
      hover: null,
    };
  },
  components: {
    BottomItems,
    Modal,
  },
};
</script>
<style scoped>
#home {
  height: 40vh;
  width: 100%;
  background-image: linear-gradient(
      to top,
      rgba(255, 0, 0, 0) 10%,
      rgba(128, 0, 128, 0) 45%,
      rgba(0, 0, 0, 0.577) 99%
    ),
    url(../assets/image-hero-desktop.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  justify-content: center;
}
nav {
  width: 80%;
  height: fit-content;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3rem;
}
nav .links {
  display: flex;
  column-gap: 3rem;
}
.links a {
  color: white;
  text-decoration: none;
  font-weight: 500;
}
#crowdfund {
  height: fit-content;
  width: 100%;
  background: #fafafa;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom: 2rem;
}
.panel-div {
  width: 40vw;
  height: fit-content;
  background: inherit;
  margin-top: 0;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  row-gap: 2rem;
  margin-top: -5rem;
}
.panel {
  width: 100%;
  background: white;
  border-radius: 12px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.131);
}
.top {
  height: fit-content;
  padding-block: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding-inline: 3rem;
  row-gap: 0.5rem;
}
.mid {
  height: 15rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  row-gap: 2.5rem;
  padding-inline: 3rem;
}
.bottom {
  height: fit-content;
  padding: 3rem;
}
h1 {
  font-weight: 700;
  font-size: 1.8rem;
}
.bar {
  width: 100%;
  background: #fafafa;
  height: 0.9rem;
  border-radius: 26px;
}
.progress {
  width: 89%;
  height: 100%;
  background: var(--moderatecyan);
  border-radius: 26px;
  animation: slide 2s cubic-bezier(0.39, 0.58, 0.57, 1);
  animation-delay: 1s;
}
@keyframes slide {
  0% {
    width: 0%;
  }
}
.mid-values {
  display: flex;
  justify-content: space-between;
}
.mid-values-item {
  width: 30%;
}
.mid-values-item {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.mid-values-item h2 {
  font-size: 2.8rem;
  width: fit-content;
}
.mid-values-item p {
  font-size: 1.1rem;
  color: var(--darkgray);
  width: fit-content;
}
.mid-values-item:nth-child(1) {
  border-right: 2px solid #f3f3f3;
  margin-right: 1rem;
  padding-right: 2rem;
}
.mid-values-item:nth-child(2) {
  border-right: 2px solid #f3f3f3;
  margin-right: 1rem;
  padding-right: 2rem;
}
.btn-group {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin-top: 2rem;
}
.back-btn {
  padding-inline: 1.5rem;
  border-radius: 50px;
  border: none;
  font-size: 1.1rem;
  outline: none;
  font-weight: 600;
  color: white;
  background: var(--moderatecyan);
  cursor: pointer;
  transition: 0.2s all ease-in-out;
}
.back-btn:hover {
  background: var(--darkcyan);
}
.bookmark-btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 1rem;
  border-radius: 50px;
  padding: 0;
  outline: none;
  border: none;
  padding-right: 1.2rem;
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--darkgray);
  background: #f1f1f1;
  width: fit-content;
}
.bookmark-btn img {
  filter: brightness(1.5) contrast(0.3) invert(0.1);
  position: relative;
  z-index: 1;
}
.checked {
  color: var(--darkcyan);
  background: #f4f8f9;
}
.checked img {
  filter: invert(36%) sepia(41%) saturate(834%) hue-rotate(129deg)
    brightness(96%) contrast(86%);
}
.mastercraft-logo {
  position: absolute;
  transform: translateY(-8.5rem);
  width: 65px;
  height: auto;
  z-index: 1;
}
.para {
  color: rgb(94, 94, 94);
  font-size: 1rem;
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
  margin-block: 1rem;
}
h6 {
  font-size: 1.4rem;
}
.modal-backdrop {
  height: 100vh;
  position: fixed;
  width: 100%;
  background: rgba(0, 0, 0, 0.495);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal {
  position: absolute;
  z-index: 11;
  background: white;
  padding: 2rem;
  width: 40vw;
  border-radius: 8px;
}
.modal-top {
  display: flex;
  justify-content: space-between;
}
.content-top {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
}
.first {
  display: flex;
  column-gap: 1rem;
}
.amount {
  font-size: 1.2rem;
  font-weight: 700;
}
.amount span {
  font-size: 1rem;
  font-weight: 400;
  color: rgb(94, 94, 94);
}
.btnclose {
  border: none;
  outline: none;
  background: none;
  cursor: pointer;
  float: right;
}
.circle {
  min-width: 1.5rem;
  height: 1.5rem;
  border-radius: 50%;
  border: 1px solid rgba(128, 128, 128, 0.533);
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
}
.center {
  background: var(--moderatecyan);
  min-width: 0.8rem;
  min-height: 0.8rem;
  border-radius: 50%;
}

.disabled {
  opacity: 0.4;
}
.modal-container {
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
}
.modal-item {
  border: 1px solid rgb(207, 205, 205);
  cursor: pointer;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  column-gap: 1rem;
  background: white;
  color: black;
  text-align: left;
  padding: 0;
}
.row {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  column-gap: 1rem;
  padding: 2rem;
}
.title {
  font-weight: 700;
  font-size: 1.1rem;
}
.modal .pledge {
  font-weight: 600;
  font-size: 1.1rem;
}
.modalItemChecked {
  border: 2px solid var(--moderatecyan);
}
/* about items */
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
.item-top {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
}
.item-bottom {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.5rem;
}
.remaining {
  font-size: 2rem;
}
.remaining span {
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
  transition: 0.2s ease-in-out all;
}
.reward-btn:hover {
  background: var(--darkcyan);
}
.nostock-btn {
  background: var(--darkgray);
  cursor: not-allowed;
}
.container button {
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
h4 {
  font-size: 1.2rem;
}
.pledge {
  color: var(--moderatecyan);
  font-weight: 400;
}
.description {
  color: rgb(94, 94, 94);
}
.input-div {
  border-top: 2px solid rgb(220, 220, 220);
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  padding-inline: 2rem;
  padding-block: 1rem;
}
.input-div p {
}
.input-div input {
  width: 4rem;
  border: none;
  text-align: center;
  outline: none;
  caret-color: var(--moderatecyan);
}
.input-div label {
  width: fit-content;
  border-radius: 50px;
  border: 2px solid rgb(220, 220, 220);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.6rem;
  font-weight: 600;
  transition: 0.2s ease-in-out all;
}
.input-div:focus-within label {
  border: 2px solid var(--moderatecyan);
}
.input-div label p {
  color: rgb(206, 206, 206);
}
.input-div button {
  background: var(--moderatecyan);
  transition: all 0.2s ease-in-out;
  border: none;
  border-radius: 50px;
  outline: none;
  color: white;
  font-size: 1rem;
  font-weight: 600;
  padding-inline: 1.5rem;
  padding-block: 0.6rem;
  width: fit-content;
}
.input-div button:hover {
  background: var(--darkcyan);
}
.end {
  display: flex;
  column-gap: 1rem;
  height: fit-content;
}
.texthover {
  color: var(--moderatecyan);
}
.hovered {
  border: 1px solid var(--moderatecyan);
}
.heading {
  display: flex;
  flex-direction: column;
  row-gap: 0.5rem;
  margin-bottom: 2rem;
}
.heading h1 {
  font-size: 1.4rem;
  font-weight: 700;
}
.heading p {
  color: rgb(94, 94, 94);
}
.thankyou-modal{
  background: white;
  width: 23vw;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 2rem;
  row-gap: 1rem;
}
.thankyou-modal img{
  width: 90px;
  margin-bottom: 1rem;
}
.thankyou-modal h2{
  font-size: 1.3rem;
}
.thankyou-modal p{
font-size: 1rem;
color: rgb(94, 94, 94);
}
.thankyou-modal button{
  color: white;
  background: var(--moderatecyan);
  border: none;
  outline: none;
  font-weight: 500;
  padding-inline: 1.6rem;
  padding-block: .7rem;
  border-radius: 50px;
  font-size: 1rem;
 cursor: pointer;
 transition: .2s ease-in-out all;
}
.thankyou-modal button:hover{
  background: var(--darkcyan);
}
</style>
