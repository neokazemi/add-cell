<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      clipped
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      clipped-left
      fixed
      app
      dense
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <nuxt-link to="/" class="page-title">
        <v-toolbar-title v-text="title"/>
      </nuxt-link>
      <v-spacer />
      <v-btn elevation="0" to="/donate">
        Donate
      </v-btn>
      <v-btn elevation="0" to="/services">
        Services
      </v-btn>
      <v-btn elevation="0" to="/about-us">
        About Us
      </v-btn>
      <v-btn elevation="0" to="/contact-us">
        Contact Us
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer
      absolute
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      drawer: false,
      items: [
        {
          icon: 'mdi-magnify',
          title: 'Search',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      right: true,
      title: 'Add Cell'
    }
  }
}
</script>

<style scoped>
.page-title {
  color: #000;
  text-decoration: none;
  margin-left: 20px;
}
</style>
