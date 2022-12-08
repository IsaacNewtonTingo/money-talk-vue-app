<template>
  <!-- <div class="imgContainer">
    <img class="logo" src="../assets/money-talk.png" />
  </div> -->
  <div class="home">
    <div class="hor">
      <form @submit.prevent="makePayment">
        <img src="../assets/lipa.png" class="lipa" />

        <div class="item">
          <label for="">Full name *</label>
          <div class="inputAndIcon">
            <input v-model="fullName" placeholder="e.g John Doe" type="text" />
          </div>
        </div>

        <div class="item">
          <label for="">Phone number *</label>
          <div class="inputAndIcon">
            <input
              v-model="phoneNumber"
              placeholder="e.g 0724657897"
              type="tel"
            />
          </div>
        </div>

        <div class="item">
          <label for="">Amount</label>
          <div class="inputAndIcon">
            <input v-model="amount" placeholder="e.g 200" type="number" />
          </div>
        </div>

        <button :disabled="isPosting">Pay now</button>
      </form>

      <div class="records">
        <div class="transItem">
          <p class="name">James Karani</p>

          <div class="details">
            <div class="tit">
              <p class="amountText">Amount</p>
              <p class="amountText">Code</p>
            </div>

            <div class="arrows">
              <p class="arrowItem">=></p>
              <p class="arrowItem">=></p>
            </div>

            <div class="det">
              <p class="ksh">KSH. 200</p>
              <p class="ksh">QJ67TFF6G0</p>
            </div>
          </div>
        </div>

        <div class="transItem">
          <p class="name">James Karani</p>

          <div class="details">
            <div class="tit">
              <p class="amountText">Amount</p>
              <p class="amountText">Code</p>
            </div>

            <div class="arrows">
              <p class="arrowItem">=></p>
              <p class="arrowItem">=></p>
            </div>

            <div class="det">
              <p class="ksh">KSH. 200</p>
              <p class="ksh">QJ67TFF6G0</p>
            </div>
          </div>
        </div>

        <div class="transItem">
          <p class="name">Aang Beifong</p>

          <div class="details">
            <div class="tit">
              <p class="amountText">Amount</p>
              <p class="amountText">Code</p>
            </div>

            <div class="arrows">
              <p class="arrowItem">=></p>
              <p class="arrowItem">=></p>
            </div>

            <div class="det">
              <p class="ksh">KSH. 200</p>
              <p class="ksh">QJ67TFF6G0</p>
            </div>
          </div>
        </div>

        <div class="transItem">
          <p class="name">White Lotus</p>

          <div class="details">
            <div class="tit">
              <p class="amountText">Amount</p>
              <p class="amountText">Code</p>
            </div>

            <div class="arrows">
              <p class="arrowItem">=></p>
              <p class="arrowItem">=></p>
            </div>

            <div class="det">
              <p class="ksh">KSH. 200</p>
              <p class="ksh">QJ67TFF6G0</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HomeView",
  components: {},
  data() {
    return {
      fullName: "",
      phoneNumber: "",
      amount: "",
      isPosting: false,
    };
  },
  methods: {
    async makePayment() {
      this.isPosting = true;
      await axios
        .post("http://localhost:8000/api/stk-push", {
          fullName: this.fullName,
          phoneNumber: this.phoneNumber,
          amount: this.amount,
        })
        .then((response) => {
          console.log(response.data);
          this.isPosting = false;
        })
        .catch((err) => {
          console.log(err);
          this.isPosting = false;
        });
    },
  },
};
</script>

<style>
.home {
  height: 100vh;
  padding: 40px 0 0 0;
}
.imgContainer {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo {
  width: 150px;
}
.hor {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}
form {
  width: 30%;
  height: 450px;
  background: linear-gradient(
    117.89deg,
    #513a59 2.86%,
    rgba(0, 28, 53, 0) 102.29%
  );
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
  border-radius: 10px;
  padding: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.lipa {
  width: 200px;
  height: 100px;
  text-align: center;
}

input {
  height: 50px;
  border-radius: 10px;
  width: 300px;
  margin: 10px 0;
  border: none;
  background: rgba(81, 58, 89, 0.23);
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.25);
  padding: 0 0 0 40px;
  color: #c0e1ff;
}
button {
  width: 100%;
  height: 50px;
  border-radius: 10px;
  margin: 20px 0;
  background: rgba(217, 0, 206, 0.23);
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.25);
  border: none;
  color: #c0e1ff;
  font-weight: 600;
}
label {
  color: #c0e1ff;
}
.records {
  width: 30%;
  height: 450px;
  background: linear-gradient(
    117.89deg,
    #513a59 2.86%,
    rgba(0, 28, 53, 0) 102.29%
  );
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
  border-radius: 10px;
  padding: 40px;
}
.transItem {
  border-bottom: solid 1px rgba(201, 201, 201, 0.1);
  padding: 0 0 10px 0;
  margin: 0 0 20px 0;
}
.details {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}
.name {
  color: #c0e1ff;
  font-size: 16px;
  margin: 0 0 20px 0;
}
.amountText {
  color: #808c98;
  font-size: 12px;
}
.arrowItem {
  color: #808c98;
}
.ksh {
  color: #c0e1ff;
  font-size: 12px;
}
</style>
