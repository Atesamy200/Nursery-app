<template>
  <div class="home">
    <nav-bar></nav-bar>

    <div
      id="carouselExampleIndicators"
      class="carousel slide"
      data-bs-ride="carousel"
    >
      <div class="carousel-indicators">
        <button
          type="button"
          data-bs-target="#carouselExampleIndicators"
          data-bs-slide-to="0"
          class="active"
          aria-current="true"
          aria-label="Slide 1"
        ></button>
        <button
          type="button"
          data-bs-target="#carouselExampleIndicators"
          data-bs-slide-to="1"
          aria-label="Slide 2"
        ></button>
        <button
          type="button"
          data-bs-target="#carouselExampleIndicators"
          data-bs-slide-to="2"
          aria-label="Slide 3"
        ></button>
      </div>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img src="../assets/head.jpg" class="d-block w-100" />
        </div>
        <div class="carousel-item">
          <img src="../assets/head.jpg" class="d-block w-100" />
        </div>
        <div class="carousel-item">
          <img src="../assets/head.jpg" class="d-block w-100" />
        </div>
      </div>
      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carouselExampleIndicators"
        data-bs-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carouselExampleIndicators"
        data-bs-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
    <v-container fluid class="grey lighten-5">
      <v-row>
        <v-col cols="12" lg="6" sm="12" md="6" class="m-auto">
          <div style="margin: 100px auto">
            <v-card class="p-2">
              <h2 class="text-center">تسجيل الدخول</h2>
              <v-form @submit.prevent="submitLogin" v-model="valid">
                <v-container>
                  <v-row>
                    <v-col cols="12" md="12" style="margin: auto">
                      <v-text-field
                        v-model="Form.email"
                        :rules="emailRules"
                        placeholder="الايميل"
                        required
                        outlined
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" md="12" style="margin: auto">
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
                        <router-link to="/SignUpForm"
                          >انشاء حساب جديد</router-link
                        >
                      </div>
                    </v-col>
                  </v-row>
                </v-container>
              </v-form>
            </v-card>
          </div>
        </v-col>
        <v-col cols="12" lg="6" sm="12" md="6" class="m-auto">
          <img src="../assets/Dep.jpg" />
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
    <v-container>
      <img class="contact-img" src="../assets/contact_2.jpg" />
    </v-container>
    <v-container>
      <div class="col-lg-6 m-auto">
        <v-card>
          <h1 class="contact-head p-2">تواصل معنا</h1>
          <p
            style="
              text-align: center;
              font-size: 20px;
              font-weight: bold;
              padding: 25px;
            "
          >
            إننا نرى أن أهم شيء في . حضانتنا هو أنها مكان آمن. ومحبوب، ومكان
            لرعاية أطفالنا وعائلاتهم، حيث أننا نحرص كل الحرص على ضمان اطلاع
            الأولياء على سياساتنا وإجراءاتنا في حضانة علم طفلك وهذه السياسات
            والإجراءات مقدمة لكم بالتفصيل في دليل الأولياء. إن كان لديكم أي
            أسئلة تتعلق بنا، فلا تترددوا في الاتصال بنا.
          </p>
          <v-form class="form" ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
              :counter="15"
              :rules="nameRules"
              label="الاسم"
              required
              reverse
              outlined
            ></v-text-field>
            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="البريد الالكتروني"
              required
              reverse
              outlined
            ></v-text-field>
            <v-text-field
              v-model="address"
              label="العنوان"
              required
              reverse
              outlined
            ></v-text-field>
            <v-text-field
              v-model="phone"
              label="رقم الهاتف"
              required
              reverse
              outlined
            ></v-text-field>
            <v-textarea
              name="input-7-1"
              filled
              outlined
              reverse
              auto-grow
              placeholder="اكتب رسالتك الخاصة هنا"
            ></v-textarea>
            <div style="text-align: right">
              <v-btn class="ma-2" color="primary"> ارسال </v-btn>
            </div>
          </v-form>
        </v-card>
      </div>
    </v-container>
    <footer-comp></footer-comp>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
import FooterComp from "@/components/FooterComp.vue";
import http from "@/axios";
export default {
  components: { NavBar, FooterComp },
  metaInfo: {
    titleTemplate: "%s | Home",
  },
  data() {
    return {
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

      name: "",
      nameRules: [
        (v) => !!v || "Name is required",
        (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
      ],
      phone: "",
      address: "",
      select: null,
      checkbox: false,
    };
  },

  methods: {
    async submitLogin() {
      try {
        await http.post("user/login", this.Form).then((response) => {
          localStorage.setItem("token", response.data.data.token);
          localStorage.setItem("info", JSON.stringify(response.data.data));
          // this.$router.push("/");
          console.log(response.data.data);
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
    font-size: 30px;
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
td {
  padding: 0 !important;
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
<style scoped>
.contact-head {
  color: #2980b9;
  text-align: center;
  font-size: 33px;
  font-weight: bold;
  margin-bottom: 15px;
}
.form {
  border: 1px solid #eee;
  border-radius: 6px;
  padding: 5%;
}
.contact-img {
  max-width: 60%;
  display: block;
  margin: auto;
  min-height: 50%;
}
.carousel-item {
  width: 1000px;
  margin: auto !important;
}
.carousel-item img {
  display: flex !important;
  flex-direction: row;
  height: 400px !important;
  width: 1200px !important;
  justify-content: center;
  align-items: center;
  transform: translate(185px, 0px);
}
</style>
