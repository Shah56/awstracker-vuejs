<template>
  <q-card class="Sales-Overview upgrade-plan" style="width: 32%">
    <q-card-section class="tatal-sales">
      <div class="tatal-head">
        <h2>Upgrade Your Plan</h2>
      </div>
      <div class="kabab-menu">
        <svg style="width: 24px;height: 24px;">
          <path fill="currentColor"
                d="M12 16a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2Z"></path>
        </svg>
      </div>
    </q-card-section>
    <p>Please make the payment to start enjoying all the features of our premium plan as soon as possible.</p>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="sales-img">
          <img src="../../assets/briefcase.png" style="width: 25px; height: 20px;" alt=""/>
        </div>
        <div class="num-sale">
          <h1>Platinum</h1>
          <h2>Upgrade Plan</h2>
        </div>
      </div>
      <div class="p-sale">
        <sup>$</sup>
        <span>5250</span>
        <small>/Year</small>
      </div>
    </q-card-section>
    <q-card-section class="paymnt-detail">
      <h2>Payment details</h2>
      <div class="sale-profit">
        <div class="sale-des">
          <div class="pymnt-profile">
            <img src="../../assets/master-card.png" style="width: 45px;height: 32px;" alt="" srcset=""/>
          </div>
          <div class="num-sale">
            <h1>Credit card</h1>
            <p>2566 xxxx xxxx 8908</p>
          </div>
        </div>
        <div class="cvv-nmb">
          <input size="1" type="text" id="" placeholder="CVV">
        </div>
      </div>
      <div class="sale-profit">
        <div class="sale-des">
          <div class="pymnt-profile">
            <img src="../../assets/credit-card.png" style="width: 45px;height: 32px;" alt="" srcset=""/>
          </div>
          <div class="num-sale">
            <h1>Credit card</h1>
            <p>8990 xxxx xxxx 6852</p>
          </div>
        </div>
        <div class="cvv-nmb" data-no-activator="">
          <input size="1" type="text" id="" placeholder="CVV">
        </div>
      </div>
    </q-card-section>
    <q-card-section class="paymnt-method">
      <a href="">Add Payment Method</a>
      <div class="input-field">
        <input placeholder="Email Address" size="1" type="text" id="" class="">
      </div>
      <button style="cursor: pointer;"> Process To Payment</button>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: "UpgradePlanStaticCard"
}
</script>

<style scoped>
html, body, div, span, h1, h2, h3, h4, h5, h6, p, a {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}

.containers {
  display: flex;
  width: 85%;
  margin: 0 auto;
  margin-top: 50px;
  flex-wrap: wrap;
  gap: 30px;
}

..upgrade-plan {
  width: 29%;
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 0 15px #D0D0D0;
  padding: 10px 20px;
}

.tatal-sales {
  align-items: center;
  display: flex;
  justify-content: space-between;
}

.upgrade-plan .tatal-head {
  margin: 10px 0px;
}

.upgrade-plan .tatal-sales h2 {
  font-size: 1.25rem;
  font-weight: 600;
}

.upgrade-plan p {
  font-size: 1rem;
  margin: 10px 0px;
}

.upgrade-plan .sale-profit {
  background-color: rgb(244, 245, 250);
  padding: 10px 10px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.sale-des {
  display: flex;
  gap: 20px;
  align-items: center;
  margin: 10px 10px;
}

.upgrade-plan .sales-img {
  border: 1px solid rgb(145, 85, 253);
  padding: 10px 10px;
  border-radius: 5px;
}

.num-sale h1 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 2rem;
}

.upgrade-plan .num-sale h2 {
  color: rgb(145, 85, 253);
}

.upgrade-plan .p-sale sup {
  font-size: .9rem;
  line-height: 1rem;
  font-weight: 400;
}

.upgrade-plan .p-sale span {
  font-size: 1.75rem;
  font-weight: 600;
}

.paymnt-detail h2 {
  font-weight: 600;
  margin-left: 10px;
  margin: 10px 0px;
}

.upgrade-plan .paymnt-detail .sale-profit {
  background-color: white;
  padding: 0;
  border-radius: none;
}

.num-sale h1 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 2rem;
}

.upgrade-plan .num-sale p {
  margin: 0;
  color: gray;
}

.cvv-nmb input {
  height: 40px;
  border-style: none;
  width: 80px;
  text-align: center;
  border-radius: 6px;
  color: grey;
  border: 1px solid grey;
}

.paymnt-method a {
  font-size: 1rem;
  text-decoration: none;
  color: rgb(145, 85, 253);
}

.paymnt-method .input-field input {
  width: 100%;
  height: 40px;
  margin: 10px 0px;
  border-style: none;
  text-align: center;
  border-radius: 6px;
  color: grey;
  border: 1px solid grey;
}

.paymnt-method button {
  width: 100%;
  height: 40px;
  margin: 10px 0px;
  border-style: none;
  text-align: center;
  border-radius: 6px;
  color: white;
  background-color: rgb(145, 85, 253);
}
</style>