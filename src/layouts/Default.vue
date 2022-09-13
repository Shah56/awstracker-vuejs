<template>
  <div>
    <q-toolbar class="bg-primary text-white toolbarSpace" style="background-color: #181414 !important; height: 85px;">

      <!--      <q-btn flat @click="drawers()" round dense icon="menu"/>-->

      <!--      <q-separator dark vertical inset/>-->

      <!--      <q-btn flat label="Stealth Connect" @click="mainPage()"/>-->
      <!--      <q-btn icon="local_fire_department"-->
      <!--             class="q-mr-sm"-->
      <!--             color="orange"-->
      <!--             flat round dense-->
      <!--             @click="launchFleet"-->
      <!--             size="xs"-->
      <!--      >-->
      <!--&lt;!&ndash;        <q-tooltip&ndash;&gt;-->
      <!--&lt;!&ndash;            content-class="bg-grey"&ndash;&gt;-->
      <!--&lt;!&ndash;            content-style="font-size: 16px"&ndash;&gt;-->
      <!--&lt;!&ndash;            :offset="[10, 10]"&ndash;&gt;-->
      <!--&lt;!&ndash;        >&ndash;&gt;-->
      <!--&lt;!&ndash;          Enable Drones&ndash;&gt;-->
      <!--&lt;!&ndash;        </q-tooltip>&ndash;&gt;-->
      <!--      </q-btn>-->

      <!--      <q-separator dark vertical/>-->
      <!--      <div v-for="item of menuItems" :key="item.label">-->
      <!--        <q-btn stretch flat-->
      <!--               :icon="item.icon"-->
      <!--               :label="item.label"-->
      <!--               :to="item.page"-->
      <!--        />-->
      <!--      </div>-->

      <q-space/>

      <!--
        notice shrink property since we are placing it
        as child of QToolbar
      -->

      <q-separator/>

      <q-btn-dropdown
          flat style="float: left">
        <template v-slot:label>
          <div class="row items-center no-wrap">
            <q-icon left name="person"/>
            <div class="text-center">
              {{ fullName }}
            </div>
          </div>
        </template>
        <q-list>
          <q-item clickable v-close-popup style="background-color: grey !important; color: #fff">
            <q-item-section @click="profileClick()">
              <q-icon left name="person"/>
              <q-item-label>Profile</q-item-label>
            </q-item-section>
          </q-item>

          <q-item clickable v-close-popup style="background-color: grey !important; color: #fff">
            <q-item-section>
              <q-icon left name="settings"/>
              <q-item-label>Settings</q-item-label>
            </q-item-section>
          </q-item>

          <q-item clickable v-close-popup @click="signOut()" style="background-color: grey !important; color: #fff">
            <q-item-section>
              <q-icon left name="exit_to_app"/>
              <q-item-label>Logout</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-btn-dropdown>
    </q-toolbar>
    <!--  For Side Bar -->
    <div class="forSideBar" id="forSideBar">
      <q-layout view="lHh Lpr lff" container style="height: 896px; border-color: #181414 !important; margin-top: -20px"
                class=" rounded-borders">
        <q-header elevated class="bg-black" style="border-color: #181414 !important;">
          <q-drawer
              v-model="drawer"
              show-if-above
              :width="300"
              :breakpoint="55"
              :mini="miniState"
              @mouseover="mouseOver()"
              @mouseout="mouseOut()"
              content-class="bg-grey-3" class="sideBarDrawer" style="padding-right: 20px!important;"
          >
            <q-scroll-area class="fit" style="background-color: #181414 !important; border-color: #181414 !important;">

              <q-list padding>

                <template>
                  <q-item v-ripple style="margin-left: 15px; margin-top: -15px; height: 60px; cursor:pointer;">
                    <q-item-section avatar>
                      <img src="../assets/TS.png" alt="" style="width: 30px; height: 30px;"/>
                    </q-item-section>
                    <q-item-section style="font-size: 20px; color: #fff; margin-bottom: 10px; margin-left: 28px">
                      Stealth Connect
                    </q-item-section>
                    <q-item-section style="float: right; margin-left: 25px; margin-top: 8px">
                      <input type="checkbox" id="toggler" @change="stateDrawerManage()"/>
                      <span class="checkmark"></span>
                    </q-item-section>
                  </q-item>
                </template>

                <template v-for="(menuItem, index) in menuList">
                  <q-item :key="index" clickable v-ripple
                          @click="itemClicked(menuItem)" :active="menuItem.check === true" active-class="activeClass"
                          style="height: 70px">
                    <q-item-section avatar>
                      <q-icon :name="menuItem.icon"
                              style="font-size: 25px; margin-right: 35px; margin-bottom: 10px;margin-left: 10px;margin-top: 12px; color: white !important;"></q-icon>
                    </q-item-section>
                    <q-item-section
                        style="font-size: 18px; color: #fff; margin-bottom: 10px; margin-left: 45px; margin-top: 12px">
                      {{ menuItem.label }}
                    </q-item-section>
                  </q-item>
                  <q-separator :key="'sep' + index" v-if="menuItem.separator"></q-separator>
                </template>

              </q-list>
            </q-scroll-area>
          </q-drawer>
        </q-header>
        <!--        <q-page-container style="margin-top: 0px">-->

        <!--          <router-view/>-->
        <!--        </q-page-container>-->
      </q-layout>

    </div>
    <div class="forContent z-max" id="forContent">
      <q-layout view="lHh Lpr lff" container style="height: 850px; border-color: #181414 !important; margin-top: -20px"
                class="shadow-2 rounded-borders">
        <q-page-container style="margin-top: 20px">

          <router-view/>
        </q-page-container>
      </q-layout>

    </div>

  </div>
</template>

<script>
import {mapState, mapGetters} from "vuex";
import {Auth} from "aws-amplify";
import {ref} from 'vue'
import logo2 from '../assets/logo2.png'
// import leftDrawer from "@/components/LeftDrawer";

export default {
  name: "default-layout",
  components: {
    // leftDrawer
    // eslint-disable-next-line vue/no-unused-components
    logo2
  },

  data() {
    return {
      photo: "",
      checkState: true,
      menuList: [
        {
          icon: 'home',
          label: 'Home',
          separator: false,
          check: true,
        },
        {
          icon: 'person_add',
          label: 'Drone',
          separator: false,
          check: false,
        },
        {
          icon: 'local_shipping',
          label: 'Track',
          separator: false,
          check: false
        },
      ],
      drawer: false,
      menuItems: [
        {
          icon: "house",
          page: "/",
          label: "Home"
        },
        {
          icon: "person_add",
          page: "agent",
          label: "Drone"
        },
        {
          icon: "local_shipping",
          page: "delivery",
          label: "Track"
        }
      ],
    };
  },
  setup() {
    return {
      drawerLeft: ref(false),
      drawerRight: ref(false),
      miniState: ref(false),
      link: ref('home')
    }
  },
  mounted() {
    document.getElementById('toggler').checked = true
    const fc = document.getElementById('forContent')
    fc.style.paddingLeft = '301px'
  },
  methods: {
    mainPage() {
      this.$router.push('/')
    },
    mouseOver() {
      const fc = document.getElementById('forContent')
      fc.style.paddingLeft = '301px'
      if (this.miniState === false && this.checkState === true) {
        this.miniState = false
      } else if (this.miniState === true && this.checkState === false) {
        this.miniState = false
      }
    },
    mouseOut() {
      const fc = document.getElementById('forContent')
      const sb = document.getElementById('forSideBar')
      if (this.checkState === true) {
        this.miniState = false
        fc.style.paddingLeft = '301px'
        sb.style.width = '17.7%'
      } else if (this.checkState === false && this.miniState === false) {
        this.miniState = true
        fc.style.paddingLeft = '55px'
        sb.style.width = '17.7%'
      } else {
        fc.style.paddingLeft = '55px'
        sb.style.width = '3.7%'
      }
    },
    stateDrawerManage() {
      var elm = document.getElementById('toggler');
      // elm.checked = !elm.checked;
      if (elm.checked === true) {
        this.miniState = false
        this.checkState = true
      } else {
        this.miniState = true
        this.checkState = false
      }
    },
    itemClicked(val) {
      if (val.label === 'Home') {
        this.$router.push('/')
      } else if (val.label === 'Drone') {
        this.launchFleet()
      } else if (val.label === 'Track') {
        console.log('Track')
      }
      let arr = [...this.menuList]
      arr.map((item) => {
        if (item.label === val.label) {
          item.check = true
        } else {
          item.check = false
        }
      })
      console.log(arr, "array")
      this.menuList = arr
      //   newLetters.map((record) => {
      //   if (record.letter === letter) {
      //     record.isActive = true;
      //   } else {
      //     record.isActive = false;
      //   }
      // });
      // setLetters(newLetters);

    },
    drawers() {
      this.drawer = !this.drawer
    },
    profileClick() {
      this.$router.push('/profile')
    },
    async signOut() {
      try {
        await Auth.signOut();
        this.$router.push("/auth");
      } catch (error) {
        console.log("error signing out: ", error);
      }
    },
    async launchFleet() {

      let url = process.env.VUE_APP_APIURL

      const currentSession = await Auth.currentSession();
      this.jwt = currentSession.getIdToken().getJwtToken();
      const options = {
        headers: {
          'authorization': this.jwt
        }
      };

      console.log(url + "launch_fleet")
      let results = await this.$http.post(url + "launch_fleet", {}, options);

      if (results.status === 200) {
        this.$q.notify({
          color: "orange",
          position: "top",
          timeout: 5000,
          icon: "local_fire_department",
          message: results.data.msg,
        })
      } else {
        this.$q.notify({
          color: "orange",
          position: "top",
          timeout: 5000,
          icon: "warning",
          message: results.data.msg,
        })
      }

    },
  },
  computed: {
    ...mapState({
      user: (state) => state.profile.user,
    }),
    ...mapGetters({
      isAuthenticated: "profile/isAuthenticated",
      firstName: "profile/firstName",
      lastName: "profile/lastName",
      email: "profile/email",
    }),
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
  },
};
</script>

<style scoped>
.toolbar {
  min-height: 60px;
}

div#forSideBar .activeClass[data-v-c6c5ef5c] {
  background: linear-gradient(98deg, #c48eff, #9155fd 94%);
  color: black;
  border-bottom-right-radius: 29px;
  border-top-right-radius: 29px;
  transform: translate(-15px, 5px);
  padding-left: 32px;

}

div#forSideBar .q-item.q-item-type.row.no-wrap.q-item--clickable.q-link {
  margin-left: -10px;
}

#profile {
  height: 130px;
  background-color: #808080;
}

#menu-collapse {
  margin-top: 5%;
}

.right-itens a,
.right-itens button {
  margin-right: 10px;
}

.fixed-bottom {
  margin-bottom: 1%;
}

.activeClass {
  background-color: #C10015;
}

.fixed-bottom a img {
  width: 25px;
  height: 25px;
}

#menu-collapse {
  margin-top: 5%;
}

.layout-padding {
  padding: 1em 4em;
}

@media screen and (max-width: 600px) {
  .layout-padding {
    padding: 1.5em 0.5em;
  }
}

.menu-enter-active,
.scale-enter {
  -webkit-animation: moveFromLeftFade 0.9s ease both;
  animation: moveFromLeftFade 0.9s ease both;
}

.menu-leave-to,
.scale-leave-active {
  -webkit-animation: moveToLeft 0.9s ease both;
  animation: moveToLeft 0.9s ease both;
}

@-webkit-keyframes moveFromLeftFade {
  from {
    opacity: 0.3;
    -webkit-transform: translateX(-100%);
  }
}

@keyframes moveFromLeftFade {
  from {
    opacity: 0.3;
    -webkit-transform: translateX(-100%);
    transform: translateX(-100%);
  }
}

@-webkit-keyframes moveToRight {
  from {
  }
  to {
    -webkit-transform: translateX(100%);
  }
}

@keyframes cartOut {
  from {
    transform: translate(0px, 0px);
  }
  to {
    transform: translate(1200px, 0px);
    animation-timing-function: ease-out;
  }
}

@-webkit-keyframes moveToLeft {
  from {
  }
  to {
    opacity: 0.5;
    -webkit-transform: translateX(-100%);
  }
}

@keyframes moveToLeft {
  from {
  }
  to {
    opacity: 0.5;
    -webkit-transform: translateX(-100%);
    transform: translateX(-100%);
  }
}

@-webkit-keyframes moveFromRight {
  from {
    opacity: 0.7;
    -webkit-transform: translateX(100%);
  }
}

@keyframes moveFromRight {
  from {
    opacity: 0.7;
    -webkit-transform: translateX(100%);
    transform: translateX(100%);
  }
}

.drawer-closer .item-content {
  margin-left: 50px !important;
}

.drawer-content .list-label {
  line-height: 45px;
}

.drawer-content .item {
  height: 45px;
}

.router-link-active .item-primary {
  color: #027be3;
}

@media only screen and (min-width: 601px) {
  .adv-form-one .timeline-badge {
    right: auto !important;
    left: auto !important;
  }

  .adv-form-one .timeline-content {
    margin-left: 3.9rem;
  }

  .adv-form-one .timeline-item {
    width: 100% !important;
  }

  .adv-form-one .timeline-title {
    text-align: inherit !important;
    margin-left: 3.9rem;
  }

  .timeline:before {
    left: 1.6rem;
  }
}

.adv-form-one .timeline-content .group .primary {
  display: none !important;
}

.underline {
  text-decoration: underline;
}

input[type='checkbox'] {
  accent-color: grey;
}

/*for side bar fix css */

.forSideBar {
  position: absolute;
  top: 52px;
  left: 0px;
  z-index: 9999999999999;
  display: block;
  min-height: 100vh;
  height: 100%;
  /*width: 300px;*/
  width: 17.7%;

}

.forContent {
  padding-left: 55px;
}

/*.forContent > .mapboxgl-control-container >  maplibregl-ctrl-top-left {*/
/*    top: 45px;*/
/*    left: 0;*/
/*    right: 10px;*/
/*    left: unset;*/
/*}*/
/*.mapboxgl-ctrl-top-left{*/
/*  top: 45px;*/
/*    left: 0;*/
/*    right: 10px;*/
/*    left: unset;*/

/*}*/
div#markmap .mapboxgl-control-container .mapboxgl-ctrl-top-left {
  top: 45px !important;
  left: 0 !important;
  right: 10px !important;
  left: unset !important;

}

.menuLink {
  color: white;
  background: #F2C037
}

.toolbarSpace {
  margin-top: 0px;
}

</style>

<style lang="sass">
.my-menu-link
  color: white
  background: #F2C037
  border-radius: 30%
</style>
