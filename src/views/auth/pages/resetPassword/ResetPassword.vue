<template>
  <v-row class="justify-center">
    <v-col  xl="4" lg="6" md="8" sm="10" xs="12">
      <v-card class="rounded-0" elevation="10">
        <v-row style="background:#ECEBEE" class="px-0 py-1 ma-0" >
          <v-col cols="12" class="top d-flex justify-center align-center">
            <img src="../../../../assets/polban.png" alt="Logo Polban"/>
            <div class="ml-2 text-subtitle-2" style="color:#272343">Politeknik Negeri Bandung</div>
          </v-col>
        </v-row>
        <v-row class="px-0 py-2  ma-0">
          <v-col cols="12" class="d-flex justify-center mt-5">
            <div style="color:#272343" class="text-h5 font-weight-bold">Lupa Password?</div>
          </v-col>
          <v-col cols="12" class="pa-0 mt-5">
            <v-form
              @submit.prevent="resetPassword()"
            >
              <v-row class="pa-0 ma-0">
                <v-col :cols="isMobile? '12' : '10'" :offset="isMobile? '0' : '1'" :class="isMobile? 'px-5' : ''" class="pt-0 mt-1">
                  <v-text-field
                    :aria-autocomplete="false"
                    dense
                    filled
                    v-model="newPassword"
                    :rules="[rules.emptyPassword, rules.minimumPassword, rules.isContainMixCase, rules.isContainNumberAndLetter, rules.isContainSpecialCharacter]"
                    :append-icon="
                          isNewPasswordShown ? 'mdi-eye' : 'mdi-eye-off'
                        "
                    :type="isNewPasswordShown ? 'text' : 'password'"
                    class="input-group--focused"
                    :color="currentTheme.colorPrimary"
                    label="Password Baru"
                    @click:append="isNewPasswordShown = !isNewPasswordShown"/>
                </v-col>
                <v-col :cols="isMobile? '12' : '10'" :offset="isMobile? '0' : '1'" :class="isMobile? 'px-5' : ''" class="pt-0 mt-1">
                  <v-text-field
                    :aria-autocomplete="false"
                    dense
                    filled
                    :color="currentTheme.colorPrimary"
                    v-model="confirmNewPassword"
                    :rules="[
                          rules.emptyPassword,
                          rules.minimumPassword,
                          rules.confirmPassword,
                        ]"
                    :append-icon="
                          isconfirmNewPasswordShown ? 'mdi-eye' : 'mdi-eye-off'
                        "
                    :type="isconfirmNewPasswordShown ? 'text' : 'password'"
                    class="input-group--focused"
                    @click:append="
                          isconfirmNewPasswordShown = !isconfirmNewPasswordShown
                        "
                    label="Konfirmasi Password Baru"
                  />
                </v-col>
                <v-col :cols="isMobile? '12' : '10'" :offset="isMobile? '0' : '1'" :class="isMobile? 'px-5' : ''" class="pt-0 mt-1">
                  <v-text-field
                    :aria-autocomplete="false"
                    dense
                    filled
                    :color="currentTheme.colorPrimary"
                    v-model="hint"
                    label="Hint Baru"
                    hint="hint adalah kata kunci yang membantu kamu saat lupa password"
                  />
                </v-col>
                <v-col cols="1" v-if="!isMobile"/>
                <v-col cols="4" offset="4" class="d-flex justify-center">
                  <v-btn
                    :color="currentTheme.colorSecondary"
                    :rules="[rules.isEmail,rules.isEmailValid]"
                    style="color: white"
                    :disabled="!isInputValid"
                    type="submit"
                  >
                    Submit
                  </v-btn>
                </v-col>
              </v-row>
            </v-form>
          </v-col>
        </v-row>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import { mapGetters } from "vuex"
export default {
  name: "ResetPassword",
  created () {
    if (!this.currentToken) {
      this.$router.push("/")
    }
  },
  data () {
    return {
      rules: {
        emptyPassword: (value) => !!value || "Password tidak boleh kosong",
        minimumPassword: (value) =>
          value.length > 8 || "Password minimal 8 karakter ",
        confirmPassword: (value) =>
          value === this.newPassword || "Password tidak sama",
        isContainMixCase: (value) =>
          (value.match(new RegExp("[A-Z]")) !== null && value.match(new RegExp("[a-z]")) !== null) || "Password harus merupakan kombinasi huruf besar dan huruf kecil",
        isContainNumberAndLetter: (value) =>
          (((value.match(new RegExp("[0-9]")) !== null))) || "Password harus memiliki setidaknya satu angka",
        isContainSpecialCharacter: (value) =>
          ((value.match(new RegExp("[!@#$%^&*]"))) !== null) || "Password harus memiliki setidaknya satu karakter special: !@#$%^&*"
      },
      newPassword: "",
      confirmNewPassword: "",
      isconfirmNewPasswordShown: false,
      isNewPasswordShown: false,
      hint: ""
    }
  },
  computed: {
    ...mapGetters({
      currentTheme: "theme/getCurrentColor"
    }),
    isMobile () {
      return this.$vuetify.breakpoint.sm || this.$vuetify.breakpoint.xs
    },
    currentToken () {
      return this.$route.query.ref
    },
    isInputValid () {
      const isNewPasswordEmpty = this.rules.emptyPassword(this.newPassword) !== true
      const isNewPasswordMinimumLength = this.rules.minimumPassword(this.newPassword) !== true
      const isConfirmPasswordEmpty = this.rules.emptyPassword(this.confirmNewPassword) !== true
      const isConfirmPasswordMinimumLength = this.rules.minimumPassword(this.confirmNewPassword) !== true
      const isPasswordSame = this.rules.confirmPassword(this.confirmNewPassword) !== true
      return !(isNewPasswordEmpty || isNewPasswordMinimumLength || isConfirmPasswordEmpty || isConfirmPasswordMinimumLength || isPasswordSame)
    }
  },
  methods: {
    async resetPassword () {
      // this.$router.push({
      //   name:
      // })
      console.log(`Mengirim email ke ${this.email}`)
    }
  }
}
</script>

<style scoped>
.top img{
  width: 40px;
  height: 40px;
}
.message-text{
  color: rgba(39,35,67,0.72);
}
</style>
