<template>
    <q-layout view="lHh Lpr fFf">
        <q-toolbar unelevated style="height: 70px" class="bg-black text-white q-my-md shadow-2">
            <div class="text-h6 q-ml-lg">Movie App</div>

            <q-space />
                <div v-if="$q.screen.md || $q.screen.md || $q.screen.lg || $q.screen.xl">
                <q-btn :to="{ name: 'Homeuser' }" color="white" size="medium" flat>Home</q-btn>
                <q-btn :to="{ name: 'myOrder' }" color="white" size="medium" flat>Pesanan Saya</q-btn>
                <q-btn color="white" size="medium" flat>Tentang</q-btn>
                <q-btn color="white" size="medium" @click="logout()" flat>Logout</q-btn>
            </div>
            <q-btn color="white" size="medium" round icon="shopping_cart" flat/>
             <q-btn flat @click="drawer = !drawer" round v-if="$q.screen.xs || $q.screen.sm" icon="menu"/>
        </q-toolbar>
        <q-drawer
               v-model="drawer"
               :width="200"
               :breakpoint="500"
                side="right"
                content-class="bg-grey-2"
            >
                <q-scroll-area class="fit">
                    <q-list padding class="menu-list">

                            <q-item  clickable v-ripple>
                                <q-item-section avatar>
                                    <q-icon name="home" />
                                </q-item-section>
                                <q-item-section>
                                    Home
                                </q-item-section>
                            </q-item>

                    </q-list>
                </q-scroll-area>
        </q-drawer>
        <q-page-container class="bg-dark">
            <router-view />
        </q-page-container>
    </q-layout>
</template>
<script>
export default {
  data () {
    return {
      drawer: false
    }
  },
  methods: {
    logout () {
      this.$q.localStorage.remove()
      this.$router.push({ name: 'LoginPage' })
    }
  }
}
</script>
