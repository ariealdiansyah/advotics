<template>
  <q-layout view="hHh lpR lFf">
    <q-header elevated class="bg-white text-grey">
      <q-toolbar>
        <q-toolbar-title>
          <img
            width="128"
            height="35"
            src="https://www.advotics.com/wp-content/uploads/2019/07/advotics-logo-optimize.jpg"
            class="custom-logo"
            alt="advotics-logo"
          />
        </q-toolbar-title>
        <div class="row justify-center text-center">
          <div class="col-12">Username</div>
          <div class="col-12">Company Name</div>
        </div>
        <q-icon name="account_circle" size="md" class="q-mr-sm" />
        <q-icon name="logout" size="md" class="q-mr-sm" />
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" :mini="mini" side="left" elevated>
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-btn flat dense round icon="menu" aria-label="Menu" />
            </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <img src="~assets/Dashboardicon.svg" style="width: 30px; height: 30px" />
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      leftDrawerOpen: false,
      mini: true,
    };
  },
  methods: {
    toggleLeftDrawer() {
      mini.value = !mini.value;
    },
  },
};
</script>
