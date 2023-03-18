<template>
  <div>
    <navbar-admin></navbar-admin>

    <v-container style="margin: auto; width: 50%">
      <h2 class="contact-head text">الشكاوي والمقترحات</h2>
      <b-table :items="items" :fields="fields" bordered>
        <template #cell(suggestion)="data">
          <div class="text">
            <p>{{ data.item.suggestion }}</p>
          </div>
        </template>
      </b-table>
    </v-container>
  </div>
</template>

<script>
import NavbarAdmin from "./NavbarAdmin.vue";
import http from "@/axios";
export default {
  name: "FaqAdmin",
  components: {
    NavbarAdmin,
  },
  data() {
    return {
      fields: [
        {
          key: "suggestion",
          label: "المقترحات والشكاوي ",
          thStyle: {
            background: "#367db5",
            color: "#fff",
            border: "1px solid",
            textAlign: "center",
          },
        },
      ],
      items: [],
    };
  },
  methods: {
    async getData() {
      try {
        await http.get("admin/suggestions").then((res) => {
          this.items = res.data.data;
        });
      } catch (e) {
        console.log(e);
      }
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

<style></style>
