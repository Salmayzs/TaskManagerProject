<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <q-avatar>
            <img src="~assets/tasks.webp" alt="task logo" />
          </q-avatar>
          Task App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-scroll-area
        style="
          height: calc(100% - 150px);
          margin-top: 150px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <EssentialLink
            v-for="link in essentialLinks"
            :key="link.title"
            v-bind="link"
          />
        </q-list>
      </q-scroll-area>
      <q-img
        class="absolute-top"
        src="https://media.istockphoto.com/id/1181693861/vector/material-design-background-diagonal-layered-overlapping-paper-in-millennial-pink-salmon-and.jpg?s=612x612&w=0&k=20&c=GkSUMB9wtdhXx-h_79DeLj7QGaMcwWmKTXd5hNgp2nE="
        style="height: 150px"
      >
        <div class="absolute-bottom bg-transparent">
          <q-avatar class="q-mb-sm" size="56px">
            <img
              src="https://cdn.everskies.com/media/avatar/6v4DG8dzfKSwAxeyliar.png"
              alt="Avatar image"
            />
          </q-avatar>
          <div class="text-weight-bold">Salma Zaleta</div>
          <div>@salma</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
    <EssentialLink />
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Home",
    icon: "home",
    link: "home",
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
