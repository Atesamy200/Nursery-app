<template>
  <div>
    <nav-bar></nav-bar>
    <v-container>
      <v-row>
        <!-- Start Card -->
        <v-col md="6" sm="12">
          <v-card
            class="mx-auto"
            style="padding: 5%; height: 100%; text-align: center; font-size:20px; line-height:2;"
            
          >
            <v-list-item>
              <v-list-item-content>
                <h2 style="font-weight: bold">بيانات أولياء الأمور</h2>
                <hr />
                <v-list-item-title> بسنت أحمد </v-list-item-title>
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >السن : 5 سنوات</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >النوع : أنثي</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >رقم الوالد : 010125478541</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >رقم الوالدة : 010125878841</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >اسم الوالد : أحمد عبد الوهاب</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1">
                  الحالة الصحية للطفل : سليم</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >اسم الوالدة : رباب عبد التواب</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >مؤهل الوالد : بكالوريوس هندسة</v-list-item-subtitle
                >
                <hr />
                <v-list-item-subtitle class="pt-1"
                  >مؤهل الوالدة : ليسانس أداب</v-list-item-subtitle
                >
                <hr />
              </v-list-item-content>
            </v-list-item>
            <v-card-actions>
              <v-btn
                style="margin: 0 auto; color: #fff"
                outlined
                rounded
                text
                @click="changeAvatar()"
              >
                تغيير الصورة
                <span class="mdi mdi-image-edit"></span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
        <!-- End Card -->
        <!-- Start Profile Info -->
        <v-col cols="12" lg="6"> 
    <additional-data></additional-data>
        </v-col>
        <!-- End Profile Info -->
      </v-row>
    <v-col md="6" sm="12">
          <v-card class="overflow-hidden" color="indigo lighten-1" dark>
            <v-toolbar flat color="indigo">
              <v-icon>mdi-account</v-icon>
              <v-toolbar-title class="font-weight-light">
                الملف الشخصي للمستخدم
              </v-toolbar-title>
              <v-spacer></v-spacer>
              <v-btn
                color="red darken-3"
                fab
                small
                @click="isEditing = !isEditing"
              >
                <v-icon v-if="isEditing"> mdi-close </v-icon>
                <v-icon v-else> mdi-pencil </v-icon>
              </v-btn>
            </v-toolbar>
            <v-container>
              <v-row>
                <v-col md="12" sm="12" class="m-auto">
                  <v-avatar
                    class="d-block m-auto"
                    style="height: 100px; min-width: 100px; width: 100px"
                  >
                    <div
                      class="seller_image"
                      :style="{
                        background: 'url(' + user_credentials.avatar + ')',
                        backgroundSize: 'contain',
                      }"
                    ></div>
                  </v-avatar>
                </v-col>
                <v-col md="6" sm="12">
                  <v-text-field
                    :disabled="!isEditing"
                    color="white"
                    label="اسم المستخدم"
                    reverse
                    v-model="userData.name"
                  ></v-text-field>
                </v-col>
                <v-col md="6" sm="12">
                  <v-text-field
                    :disabled="!isEditing"
                    color="white"
                    label="البريد الالكتروني "
                    reverse
                    v-model="userData.email"
                  ></v-text-field>
                  <v-text-field
                    :disabled="!isEditing"
                    color="white"
                    label="السن"
                    value="5"
                    reverse
                  ></v-text-field>
                  <v-text-field
                    :disabled="!isEditing"
                    color="white"
                    label="العنوان"
                    value="القاهره"
                    reverse
                  ></v-text-field>
                </v-col>
                <v-card-text
                  style="display: flex; justify-content: space-around"
                >
                  <v-col md="5" sm="12">
                    <v-text-field
                      :disabled="!isEditing"
                      color="white"
                      label="رقم الهاتف"
                      reverse
                      v-model="userData.phone"
                    ></v-text-field>
                  </v-col>
                </v-card-text>
              </v-row>
            </v-container>
            <v-divider></v-divider>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn :disabled="!isEditing" color="success" @click="save">
                حفظ
              </v-btn>
            </v-card-actions>
            <v-snackbar v-model="hasSaved" :timeout="2000" absolute bottom left>
              تم تحديث معلوماتك الشخصية بنجاح
            </v-snackbar>
          </v-card>
        </v-col>
    
    </v-container>
    <footer-comp></footer-comp>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
import AdditionalData from "@/components/AdditionalData.vue";
import FooterComp from "@/components/FooterComp.vue";
export default {
  name: "ProfileView",
  components: { NavBar, FooterComp, AdditionalData },
  data() {
    return {
      user_credentials: {
        avatar: "https://unsplash.it/100/100",
      },
      hasSaved: false,
      isEditing: null,
      model: null,
    };
  },
  methods: {
    customFilter(item, queryText) {
      const textOne = item.name.toLowerCase();
      const textTwo = item.abbr.toLowerCase();
      const searchText = queryText.toLowerCase();

      return (
        textOne.indexOf(searchText) > -1 || textTwo.indexOf(searchText) > -1
      );
    },
    save() {
      this.isEditing = !this.isEditing;
      this.hasSaved = true;
    },
  },
  computed: {
    userData() {
      return this.$store.getters.userInfo;
    },
  },
};
</script>

<style scoped>
.seller_image {
  width: 100%;
  height: 100%;
}
</style>
