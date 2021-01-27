<template>
  <div class="login-form">
    <form>
      <div class="innerBox">
        <label>CARD NUMBER</label>
        <input class="cardNumber" />
        <label>CARD HOLDER'S NAME</label>
        <input class="name" />
        <div class="box1">
          <div id="valid-p">
            <label>VAILD THUR</label> <br>
            <input class="validThur" />
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
</template>


<script>
export default {
  name: "LoginForm",
  data() {
    return {};
  },
};
</script>

<style>


.innerBox {
  color: black;
  display: flex;
  
  flex-direction: column;
}
.box1 {
  display: flex;
  flex-wrap: wrap;
}
label{
  font-size: 15px;
}

#ccv-p{
  padding-left: 62px;
}
.validThur{width: 120%;}
.ccv{width: 120%;}

input {
  width: 400px;
  height: 50px;
  border-radius: 10px;
}
button {
  width: 400px;
  height: 50px;
  color: white;
  background: black;
  margin-top: 15px;
  border-radius: 10px;
  
}
</style>

