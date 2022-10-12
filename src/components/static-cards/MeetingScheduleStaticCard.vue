<template>
  <q-card class="Sales-Overview meeting-shdl" style="width: 31%">
    <q-card-section class="tatal-sales">
      <div class="tatal-head">
        <h2>Meeting Schedule</h2>
      </div>
      <div class="kabab-menu">
        <svg style="width: 24px;height: 24px;">
          <path fill="currentColor"
                d="M12 16a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2Z"></path>
        </svg>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="profile">
          <img src="../../assets/profile.png" style="width:38px;height: 38px;" alt="" srcset="">
        </div>
        <div class="num-sale">
          <h2>Call with Woods</h2>
          <span><q-icon name="today"/>  21 Jul | 08:20-10:30</span>
        </div>
      </div>
      <div class="p-sale">
        <span class="year">Year of 2021</span>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: "MeetingScheduleStaticCard"
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

.meeting-shdl {
  width: 29%;
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 0 15px #d0d0d0;
  padding: 10px 20px;
}

.tatal-sales {
  align-items: center;
  display: flex;
  justify-content: space-between;
}

.tatal-head h2 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 1.5rem;
}

.sale-profit {
  align-items: center;
  margin: 22px 0px;
  display: flex;
  justify-content: space-between;
}

.sale-des {
  display: flex;
  align-items: center;
  gap: 20px;
}

.profile {
  display: flex;
  margin-top: 10px;
  gap: 2px;
  align-items: center;
}

.meeting-shdl .profile img {
  border-radius: 50%;
}

.meeting-shdl .num-sale h2 {
  font-weight: 600;
  font-size: 1rem;
  line-height: 2rem;
}

.p-sale span {
  background-color: rgba(145, 85, 253, 0.2);
  color: rgb(145, 85, 253);
  font-size: .75rem;
  border-radius: 15px;
  padding: 8px 10px;
}
</style>