<template>
  <div class="column justify-center q-pa-lg forPadding"
       style="background-color: #40444f; width: 100%; position:fixed !important;">
    <!-- <q-card square class="shadow-24" style="width:300px;height:485px;"> -->
    <div class="stealthMain">
      <div class="stealthLeft">
        <h2 class="stealthHeading">STEALTH CONNECT</h2>
        <h5 style="font-family: 'arial'; margin-top: 10px; font-size: 1.75rem; color: white">Cyber Security Portal</h5>
        <p style="font-size: 1.25rem; color: white">Introducing TOM SHAW’s latest creation: Stealth Connect. A
          two-part cyber-security <br/> world-first protecting
          governments and <br/> enterprises from the end point to the board room.</p>
      </div>
      <div class="stealthMiddle">
        <img src="https://noble1webapp.s3.ap-southeast-2.amazonaws.com/img/center-bg.png" alt="midImage"
             class="backImageForgot"/>
        <div class="learnMoreForgot">
          <div class="innerCircle">
            <p style="margin-top: -15px;">Learn More</p>
          </div>
        </div>
      </div>
      <div class="stealthRight">
        <q-card-section style="margin-bottom: 20px">
          <h4 class="text-h4 text-center q-my-sm" style="color: white">Forget Password</h4>
        </q-card-section>

        <q-card v-if="formState === 'forgotPassword'" square class="shadow-24" style="width:100%;padding: 50px 30px; background-color: #40444f !important;">
          <q-card-section>
            <q-form>
              <q-input
                  square clearable
                  v-model="form.username"
                  clear-icon="close"
                  type="email"
                  dark
                  color="white"
                  label="Email">
                <template v-slot:prepend>
                  <q-icon name="email"/>
                </template>
              </q-input>
            </q-form>
          </q-card-section>
          <q-card-section class="text-center q-pa-sm" v-if="hasPasswordError">
            <q-btn size="sm" color="red" icon="highlight_off" :label="passwordError" @click="hasPasswordError=false"/>
          </q-card-section>
          <q-card-actions class="q-px-lg">
            <q-btn unelevated size="lg" @click="forgotPassword" class="bg-grey full-width text-white" label="SUBMIT"/>
          </q-card-actions>
          <q-card-section class="text-center q-pa-sm">
            <q-btn flat size="sm" @click="toggleLogin" color="white" label="Back to Sign In page."/>
          </q-card-section>
        </q-card>

        <q-card v-if="formState === 'forgotPasswordSubmit'" square class="shadow-24">
          <q-card-section class="bg-grey-8 text-white">
            <div class="text-h6">Confirmation</div>
            <div class="text-subtitle2">A confirmation code was sent to <span class="text-bold"> {{
                form.email
              }}. </span> Please, check your email.
            </div>
          </q-card-section>
          <q-card-section>
            <q-form>
              <q-input
                  square clearable
                  v-model="form.authCode"
                  clear-icon="close"
                  label="Authentication Code">
                <template v-slot:prepend>
                  <q-icon name="input"/>
                </template>
              </q-input>
              <q-input
                  square clearable
                  v-model="form.password"
                  clear-icon="close"
                  type="password"
                  label="New Password"
              >
                <template v-slot:prepend>
                  <q-icon name="lock"/>
                </template>
              </q-input>
            </q-form>
          </q-card-section>
          <q-card-section class="text-center q-pa-sm" v-if="hasPasswordError">
            <q-btn size="sm" color="red" icon="highlight_off" :label="passwordError" @click="hasPasswordError=false"/>
          </q-card-section>
          <q-card-actions class="q-px-lg">
            <q-btn unelevated size="lg" @click="forgotPasswordSubmit" class="bg-teal full-width text-white"
                   label="SUBMIT"/>
          </q-card-actions>
        </q-card>

      </div>
    </div>


  </div>
</template>


<script>
import {Auth} from 'aws-amplify'

export default {
  name: 'SignUp',
  data() {
    return {
      formState: 'forgotPassword',
      hasPasswordError: false,
      passwordError: '',
      form: {
        password: '',
        username: '',
        given_name: '',
        family_name: '',
        authCode: ''
      }
    }
  },
  methods: {
    async forgotPassword() {
      try {
        this.form.email = this.form.username;
        const {username} = this.form
        await Auth.forgotPassword({
          username
        })
        this.formState = 'forgotPasswordSubmit'
      } catch (error) {
        this.passwordError = error.message
        this.hasPasswordError = true;
      }
    },
    async forgotPasswordSubmit() {
      try {
        const {username, authCode} = this.form
        await Auth.forgotPasswordSubmit(username, authCode)
        this.$q.notify({
          color: "teal",
          icon: "thumb_up",
          message: "Your password has been reset successfully!",
          position: "right"
        });
        this.$router.push("/auth");
      } catch (error) {
        this.passwordError = error.message
        this.hasPasswordError = true;
      }
    },
    toggleLogin() {
      this.$router.push("/auth");
    }
  }
}
</script>

<style scoped>
.forPadding {
  padding: 0 120px 100px;
}

.stealthMain {
  display: flex;
  justify-content: space-between;
  /*align-items: center;*/
  gap: 5%;
}

.stealthLeft {
  width: 40%;
  padding-top: 120px;
}

.stealthMiddle {
  width: 30%;
  position: relative;
}

.inputText {
  font-size: 32px;
}

.stealthRight {
  width: 40%;
  /*margin-top: -70px;*/
  padding-top: 120px;
}

.signUp {
  font-size: 20px;
  margin-left: 30px;
  margin-top: 10px;
  cursor: pointer;
  color: white;
}

.inputValColor {
  color: white;
}

.stealthHeading {
  font-family: 'Agency Gothic CT Bold';
  margin-bottom: 0px;
  font-size: 70px;
  font-weight: 500;
  color: white
}

.learnMoreForgot {
  display: inline-block;
  /* margin-top: -681px; */
  /* margin-right: 80px; */
  border-radius: 50%;
  /* padding: 65px; */
  color: white;
  border: 1px solid white;
  font-size: 35px;
  background-color: #40444f;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-62%, -25%);
  height: 255px;
  width: 255px;
  text-align: center;
  padding-top: 95px;
}

.innerCircle {
  display: inline-block;
  /* margin-top: -681px; */
  /* margin-right: 80px; */
  border-radius: 50%;
  /* padding: 65px; */
  color: white;
  border: 10px solid grey;
  font-size:25px;
  background-color: #40444f;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  height: 211px;
  width: 211px;
  text-align: center;
  padding-top: 95px;
}

.backImageForgot {
  width: 70%;
  height: 115%;
  margin-left: 20px;
  /*margin-top: -120px*/
}

.q-btn .q-focus-helper {
  display: none;
}
</style>