<template>
  <!-- <q-layout view="lHh Lpr lFf"> -->
  <q-layout view="hHh lpr lFf">

    <q-drawer v-model="leftDrawerOpen" bordered overlay="true">
      <q-list>
        <q-item-label header>
          <img
            src="~assets/logoblack250x250.png"
            style="width: 59px; height: 59px; margin-left: 100px"
          />
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>



    <q-page-container>
      <router-view />
    </q-page-container>


    <!-- <q-page-container> -->
    <q-page-sticky position="top-right" :offset="[20, 20]">
      <q-btn
        flat
        dense
        round
        icon="menu"
        aria-label="Menu"
        @click="toggleLeftDrawer"
      />
    </q-page-sticky>
    <!-- </q-page-container> -->
    
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "home",
    caption: "",
    icon: "home",
    link: "/",
  },
  {
    title: "about",
    caption: "",
    icon: "info",
    link: "#",
  },
  {
    title: "testimonials",
    caption: "",
    icon: "chat",
    link: "#",
  },
  {
    title: "blog",
    caption: "",
    icon: "info",
    link: "#",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
