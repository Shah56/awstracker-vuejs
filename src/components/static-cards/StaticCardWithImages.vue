<template>
  <q-card>
    <q-card-section class="rating">
      <div class="l-content">
        <h3>Ratings</h3>
        <h4>13K <span>+38%</span></h4>
        <span class="year">Year of 2021</span>
      </div>
      <div class="rat-img" v-if="statTitle==='Trainings'">
        <img src="../../assets/9.png" alt="" style="height: 190px; width: 109px">
      </div>
      <div class="rat-img" v-else>
        <img src="../../assets/10.png" alt="" style="height: 190px; width: 109px">
      </div>
    </q-card-section>
  </q-card>
</template>

<script>

export default {
  name: "StaticCardWithImages",
  props: {
    statTitle: {type: String, default: ''},
    statistics: {type: String, default: ''},
    change: {type: String, default: ''},
    chipText: {type: String, default: ''},
    chipColor: {type: String, default: ''},
    avatar: {type: String, default: ''},
    avatarWidth: {type: String, default: ''},
  },
  data() {
    return {
      avatar1: require('../../assets/9.png'),
      avatar2: require('../../assets/10.png'),
    }
  },

  created() {
    console.log(this.statTitle, "this.Avatar")

  },
  setup() {
    const checkChange = value => {
      const firstChar = value.charAt(0)
      if (firstChar === '+') {
        return true
      }

      return false
    }

    return {checkChange}
  },
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

.rating {
  border-radius: 6px;
  box-shadow: 0 0 15px #d0d0d0;
  display: flex;
  margin-top: 50px;
}

.l-content {
  padding: 25px 20px;
}

.l-content h3 {
  font-size: 1.25rem;
  line-height: 1.25rem;
  font-weight: 500;
  margin-bottom: 16px;
}

.l-content h4 {
  font-weight: 500;
  line-height: 2rem;
  font-size: 1.76rem;
  margin-bottom: 15px;
  margin-top: 20px;
}

.l-content h4 span {
  font-size: 1rem;
  font-weight: 400;
  margin-left: 10px;
  color: rgb(86, 202, 0);
}

.l-content span.year {
  height: 26px;
  background-color: rgba(145, 85, 253, 0.2);
  color: rgb(145, 85, 253);
  font-size: .75rem;
  border-radius: 10px;
  padding: 5px 10px;
}

.rat-img {
  margin-top: -23px;
}
.q-card{
  box-shadow: none;
}
</style>