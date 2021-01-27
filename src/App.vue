<template>
  <div id="app" class="centered">
    <div class="new-card-panel">
      <h1>Add New Bank Card</h1>
      <h4>New Card</h4>
    </div>
    <div class="card-item">
      <div class="card-item__side -front">
        <div class="card-item__wrapper">
          <div class="card-item__top">
            <img src="./assets/img/chip-dark.svg" class="card-item__chip" />
            <div class="card-item__type">
              <img
                src="./assets/img/vendor-bitcoin.svg"
                alt=""
                class="card-item__typeImg"
              />
            </div>
          </div>
          <label for="cardNumber" class="card-item__number">
            <span
              ><div class="card-item__numberItem">{{ cardNumber }}</div></span
            >
          </label>
          <div class="card-item__content">
            <label for="cardName" class="card-item__info"
              ><div class="card-item__holder">Card Holder's Name</div>
              <div class="card-item__name"> {{ cardHolderName }} </div></label
            >
            <div class="card-item__date">
              <label for="cardMonth" class="card-item__dateTitle"
                >Valid Thru</label
              >
              <label for="cardMonth" class="card-item__dateItem"
                ><span>MM</span></label
              >
              /
              <label for="cardYear" class="card-item__dateItem"
                ><span>YY</span></label
              >
            </div>
          </div>
        </div>
      </div>
    </div>

    <div id="credit-card-form">
      <form>
        <div class="innerBox">
          <label for="cardNumber" ref="cardNumber">CARD NUMBER</label>
          <input
            type="text"
            id="cardNumber"
            v-model="cardNumber"
            v-on:keydown="replaceHash"
            autocomplete="off"
            class="card-input__input"
          />
          <label>CARD HOLDER'S NAME</label>
          <input class="name" type="text" v-model="cardHolderName" id="cardHolderName"/>
          <div class="box1">
            <div id="valid-p">
              <label>VAILD THUR</label> <br />
              <input type="text" v-model="validThur" id="validThur" class="validThur" />
            </div>
            <div id="ccv-p">
              <label>CCV</label> <br />
              <input class="ccv" />
            </div>
          </div>
          <label>VENDOR</label>
          <input class="vendor" />
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
      validThur: ""
    };
  },
  methods: {
    replaceHash(e) {
      

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
  max-width: 430px;
  height: 270px;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  z-index: 2;
  width: 100%;
  background-color: gray;
  border-radius: 15px;
  margin-bottom: 25px;
}

.card-item__side {
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 20px 60px 0 rgba(14, 42, 90, 0.55);
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
  text-shadow: 7px 6px 10px rgba(14, 42, 90, 0.8);
  user-select: none;
}

.card-item__top {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  margin-bottom: 40px;
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
  color: #fff;
  font-size: 27px;
  margin-bottom: 15px;
  display: inline-block;
  padding: 10px 15px;
  cursor: pointer;
}

.card-item__numberItem {
  width: 410px;
  display: inline-block;
}

.card-item__content {
  color: #fff;
  display: flex;
  align-items: flex-start;
}

.card-item__info {
  color: #fff;
  width: 100%;
  max-width: calc(100% - 85px);
  padding: 10px 15px;
  font-weight: 500;
  display: block;
  cursor: pointer;
}

.card-item__holder {
    opacity: 0.7;
    font-size: 13px;
    margin-bottom: 6px;
}

.card-item__name {
    font-size: 18px;
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
  width: 100px;
  white-space: nowrap;
  flex-shrink: 0;
  cursor: pointer;
}

.card-item__dateTitle {
  opacity: 0.7;
  font-size: 13px;
  padding-bottom: 6px;
  width: 100%;
}

.card-item__dateItem {
  position: relative;
}

.innerBox {
  color: black;
  display: flex;

  flex-direction: column;
}
.box1 {
  display: flex;
  flex-wrap: wrap;
}
label {
  font-size: 15px;
}

#ccv-p {
  padding-left: 62px;
}
.validThur {
  width: 120%;
}
.ccv {
  width: 120%;
}

input {
  width: 400px;
  height: 50px;
  border-radius: 10px;
}
.addCard-btn {
  width: 400px;
  height: 50px;
  color: white;
  background: black;
  margin-top: 15px;
  border-radius: 10px;
  margin-bottom: 20px;
}
</style>
