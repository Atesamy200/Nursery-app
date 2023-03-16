<template>
  <div class="home">
    <nav-bar></nav-bar>
    <v-carousel style="height: 40vh" hide-delimiters>
      <v-carousel-item
        v-for="(item, i) in items"
        :key="i"
        :src="item.src"
      ></v-carousel-item>
    </v-carousel>
    <v-container fluid class="grey lighten-5">
      <v-row>
        <v-col cols="12" lg="12" sm="12" md="12" class="m-auto">
          <img src="../assets/Dep.jpg" />
        </v-col>
        <v-col cols="12" lg="12" sm="12" md="12" class="m-auto">
        <div style="margin:100px auto;">
          <v-card class="p-2">
          <h2 class="text-center">تسجيل الدخول</h2>
          <v-form @submit.prevent="submitLogin" v-model="valid">
            <v-container>
              <v-row>
                  <v-col cols="12" md="12" style="margin:auto;">
                    <v-text-field
                      v-model="Form.email"
                      :rules="emailRules"
                      placeholder="الايميل"
                      required
                      outlined
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" md="12" style="margin:auto;">
                    <v-text-field
                      v-model="Form.password"
                      :rules="passRules"
                      placeholder="كلمة المرور"
                      required
                      outlined
                      type="password"
                    ></v-text-field>
                    <p>{{ userError }}</p>
                  </v-col>
                  <v-col>
                    <div class="d-flex justify-content-between">
                      <button>تسجيل الدخول</button>
                      <router-link to="/SignUpForm">انشاء حساب جديد</router-link>
                    </div>
                  </v-col>
              </v-row>
              </v-container>
          </v-form>
          </v-card>
        </div>
        </v-col>
        <v-col cols="12" lg="12" sm="12" md="12" class="m-auto">
          <div class="box">
            <h2>علم طفلك</h2>
            <p>
              "مرحباً "إنه لشرف عظيم لنا في أن نعرف كل طفل على حدة ونعمل على
              مساعدتهم للوصول إلى أقصى إمكاناتهم" الآباء الأولياء هم شركاؤنا،
              لذا يساعدنا التواصل المستمر معهم على تلبية الاحتياجات الاجتماعية
              والبدنية، والعاطفية لجميع الأطفال." ترحب حضانة علم طفلك بصدر رحب
              بالأولياء وتتطلع لأن تكونوا جزءًا مشاركا فيما يتعلق بنمو أطفالكم
              نموهم العقلي والعاطفي، والبدني والاجتماعي. ولهذا السبب فإننا نركز
              على العمل مع الأولياء لمعرفة المزيد عن شخصية أطفالهم. الحضانة
              مفتوحة من الأحد إلى الخميس من الساعة 6:00 صباحاً وحتى 3:00 مساءً،
              بالإضافة إلى ساعات إضافية من الساعة 3:00 مساءً وحتى 5:00 مساءً.
              يرجى الاطلاع على معلوماتنا التفصيلية بخصوص ما يلزم إحضاره إلى
              الحضانة لكي نجعل الاستقرار عند انتقال طفلكم أمراً سلسا بقدر
              الإمكان."
            </p>
            <button>المزيد ..</button>
          </div>
        </v-col>
        <v-col cols="12" lg="12" sm="12" md="12" class="m-auto">
          <video
            poster="../assets/t3.jpeg"
            class="p-5"
            src="../assets/Video.mp4"
            controls
          ></video>
        </v-col>
      </v-row>
    </v-container>
    
    <footer-comp></footer-comp>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
import FooterComp from "@/components/FooterComp.vue";
import http from "@/axios"
export default {
  components: { NavBar, FooterComp },
  metaInfo: {
    titleTemplate: "%s | Home",
  },
  data() {
    return {
      items: [
        {
          src: "data:image/jpeg;base64,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",
        },
        {
          src: "https://t3.ftcdn.net/jpg/03/20/81/98/360_F_320819860_ScgqmR8DaFQLGCcg4Gq638ZorwgEpcX8.jpg",
        },
        {
          src: "https://tootris.com/edu/wp-content/uploads/2020/04/difference-between-kinder-1200x675.png",
        },
        {
          src: "https://learningexperience.ca/wp-content/uploads/2021/09/calgary-kindergarten-1.jpg",
        },
      ],
      valid: false,
    Form: {
      email: "",
      password: "",
    },
    userError: null,
    passRules: [
      (v) => !!v || "Password is required",
      (v) => v.length <= 10 || "Password must be less than 10 characters",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+/.test(v) || "E-mail must be valid",
    ],
    };
  },

  methods: {
    async submitLogin() {
      try {
        await http.post("user/login", this.Form).then((response) => {
          localStorage.setItem("token", response.data.data.token);
          localStorage.setItem("info", JSON.stringify(response.data.data));
          // this.$router.push("/");
          console.log(response.data.data)
        });
      } catch (e) {
        if (e.data.errors) {
          this.userError = "برجاء التأكد من صحة بياناتك";
        } else {
          console.log(e.data);
        }
      }
    },
  },

};
</script>

<style lang="scss">
main,
.v-main {
  background-image: url("../assets/t1.jpeg");
  background-size: cover;
  width: 100%;
}
.our-team {
  background-image: url("../assets/t2.jpeg");
  background-size: cover;
  width: 100%;
}
video,
img {
  max-width: 100%;
}
.box {
  h2 {
    text-align: center;
    font-size: 25px;
    font-weight: bold;
    color: #0d6efd;
  }
  p {
    line-height: 2;
    text-align: center;
    color: #333;
    font-size:30px;
  }
  button {
    background: #0d6efd;
    padding: 10px;
    color: #fff;
    font-weight: bold;
    display: block;
    margin: auto;
  }
}
td{
  padding: 0  !important;
}
button {
  background: #6200ea;
  padding: 10px;
  color: #fff;
  font-weight: bold;
  display: block;
  margin: auto;
}
</style>
