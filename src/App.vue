<template>
  <div id="app" class="centered">
    <div class="new-card-panel">
      <h1 class="text-uppercase">
        Add a new <br />
        bank card
      </h1>
      <h4 class="text-uppercase dim-opacity">New Card</h4>
    </div>
    <div class="card-item">
      <div class="card-item__side -front">
        <div class="card-item__wrapper">
          <div class="card-item__top">
            <img src="./assets/img/chip-dark.svg" class="card-item__chip" />
            <div class="card-item__type">
              <img src="./assets/img/vendor-bitcoin.svg" alt="" class="card-item__typeImg">
            </div>
          </div>
          <label for="cardNumber" class="card-item__number">
            <span
              ><div class="card-item__numberItem">{{ cardNumber }}</div></span
            >
          </label>
          <div class="card-item__content">
            <label for="cardName" class="card-item__info"
              ><div class="card-item__holder">CardHolder Name</div>
              <div class="card-item__name">{{ cardHolderName }}</div></label
            >
            <div class="card-item__date">
              <label for="cardMonth" class="card-item__dateTitle"
                >Valid Thru</label
              >
              <label for="cardMonth" class="card-item__dateItem"
                ><span>{{ validThur }}</span></label
              >
              <label for="cardYear" class="card-item__dateItem"
                ><span></span
              ></label>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div id="credit-card-form">
      <form>
        <div class="innerBox">
          <label for="cardNumber">CARD NUMBER</label>
          <input
            type="text"
            id="cardNumber"
            ref="cardNumber"
            v-model="cardNumber"
            autocomplete="off"
            class="card-input__input"
            :maxlength="maxCard"
          />
          <label>CARDHOLDER NAME</label>
          <input
            class="name card-input__input"
            type="text"
            v-model="cardHolderName"
            id="cardHolderName"
          />
          <div class="box1">
            <div id="valid-p">
              <label>VAILD THUR</label> <br />
              <input
                type="text"
                v-model="validThur"
                id="validThur"
                class="validThur card-input__input"
              />
            </div>
            <div id="ccv-p">
              <label>CCV</label> <br />
              <input
                class="ccv card-input__input"
                type="password"
                v-model="ccv"
                :maxlength="3"
              />
            </div>
          </div>
          <label for="vendors">VENDOR</label>
          <select
            name="vendors"
            class="vendors card-input__input -select"
            v-on:change="onChangeVendor($event)"
          >
            <option value="" disabled="disabled" selected="selected"></option>
            <option value="bitcoin">Bitcoin Inc</option>
            <option value="ninja">Ninja Bank</option>
            <option value="blockchain">Block Chain Inc</option>
            <option value="evil">Evil Corp</option>
          </select>
        </div>

        <button class="addCard-btn">Add Card</button>
      </form>
    </div>

    <router-view />
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      cardNumber: "",
      cardHolderName: "",
      validThur: "",
      ccv: "",
      vendors: "",
      maxCard: 19
    };
  },
  methods: {
    replaceHash(e) {},
    cardNumberSpace: function () {
      var cardNumber = this.$refs.cardNumber.value;
      cardNumber.replace(/^(.{4})(.{4})(.{4})(.*)$/, " ");
    },
    onChangeVendor: function(e){
        var id = e.target.value;
        console.log(id)
    },
  },
};
</script>

<style>
#app {
  color: #2c3e50;
  display: flex;
  flex-flow: column;
}
#activeCard {
  display: flex;
  height: 250px;
  width: 400px;
  color: red;
  background-color: lightgray;
  border-radius: 15px;
  margin-bottom: 20px;
}

.new-card-panel {
  text-align: center;
}
.chipImg {
  margin: 20px;
}

.card-item {
  max-width: 400px;
  height: 250px;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  z-index: 2;
  width: 100%;
  background-color: lightgray;
  border-radius: 15px;
  margin-bottom: 25px;
}

.card-item__side {
  border-radius: 15px;
  overflow: hidden;
  transform: perspective(2000px) rotateY(0deg) rotateX(0deg) rotate(0deg);
  transform-style: preserve-3d;
  transition: all 0.8s cubic-bezier(0.71, 0.03, 0.56, 0.85);
  backface-visibility: hidden;
  height: 100%;
}

.card-item__wrapper {
  font-family: "Source Code Pro", monospace;
  padding: 25px 15px;
  position: relative;
  z-index: 4;
  height: 100%;
  user-select: none;
}

.card-item__top {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  margin-bottom: 20px;
  padding: 0 10px;
}

.card-item__chip {
  width: 40px;
}

.card-item__typeImg {
  max-width: 100%;
  object-fit: contain;
  max-height: 100%;
  object-position: top right;
}

.card-item__number {
  font-weight: 500;
  line-height: 1;
  margin-bottom: 10px;
  display: inline-block;
  padding: 10px 5px;
  font-size: 2rem;
}

.card-item__numberItem {
  width: 410px;
  display: inline-block;
  color: black;
}

.card-item__content {
  display: flex;
  align-items: flex-start;
}

.card-item__info {
  width: 100%;
  max-width: calc(100% - 85px);
  padding: 10px 10px;
  font-weight: 500;
  display: block;
  cursor: pointer;
}

.card-item__holder {
  opacity: 0.7;
  color: black;
  font-size: 15px;
  margin-bottom: 6px;
  text-transform: uppercase;
}

.card-item__name {
  font-size: 18px;
  color: black;
  line-height: 1;
  white-space: nowrap;
  max-width: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
  text-transform: uppercase;
}

.card-item__date {
  flex-wrap: wrap;
  font-size: 18px;
  margin-left: auto;
  padding: 10px;
  display: inline-flex;
  width: 107px;
  white-space: nowrap;
  flex-shrink: 0;
  cursor: pointer;
}

.card-item__dateTitle {
  opacity: 0.7;
  color: black;
  font-size: 15px;
  padding-bottom: 6px;
  width: 100%;
  text-transform: uppercase;
}

.card-item__dateItem {
  position: relative;
  font-size: 18px;
  color: black;
  text-transform: uppercase;
}

.card-input__input.-select {
  -webkit-appearance: none;
  background-image: url("./assets/img/arrow-down.png");
  background-size: 12px;
  background-position: 95% center;
  background-repeat: no-repeat;
  padding-right: 30px;
  size: 100%;
}

.card-input__input {
  width: 100%;
  height: 50px;
  border-radius: 5px;
  box-shadow: none;
  border: 1px solid #242629;
  transition: all 0.3s ease-in-out;
  font-size: 18px;
  padding: 5px 15px;
  background: none;
  color: #000000;
  font-family: "Source Sans Pro", sans-serif;
}

.innerBox {
  color: black;
  display: flex;
  flex-direction: column;
}

.innerBox label {
  opacity: 0.7;
}
.box1 {
  display: flex;
  flex-wrap: wrap;
}

label {
  font-size: 15px;
}

#ccv-p {
  padding-left: 40px;
}
.validThur {
  width: 180px;
}
.ccv {
  width: 180px;
}

input {
  width: 400px;
  height: 50px;
  border-radius: 10px;
  font-size: 1rem;
  margin-bottom: 0.5rem;
  -webkit-appearance: none;
}
select {
  width: 400px;
  height: 50px;
  border-radius: 10px;
  font-size: 1rem;
}

.addCard-btn {
  width: 400px;
  height: 50px;
  color: white;
  background: black;
  margin-top: 25px;
  border-radius: 10px;
  margin-bottom: 20px;
  text-transform: uppercase;
  font-size: 1rem;
  cursor: pointer;
}

.text-uppercase {
  text-transform: uppercase;
}

.dim-opacity {
  opacity: 0.7;
}
</style>
