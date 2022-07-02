<template>
    <div>
        <v-app-bar
        fixed
        color="#f5cce7"
        hide-on-scroll
        :scroll-threshold="10"
        dark
        >
            <div v-if="width > 300" class="logo-icon" >
                <img class="logo-img" src="../assets/logo.svg" />
            </div>
            <v-spacer></v-spacer>
            <v-btn color="#520038" text rounded large style="margin-right: 5px" @click="goToStore">Купить</v-btn>
            <v-btn color="#520038" text rounded large @click="goToAbout">О нас</v-btn>
        </v-app-bar>
        <div style="height: 48px;"></div>
    </div>
</template>

<script>
export default {
  name: 'NavBar',
  props: [],
  data: () => ({
    width: window.innerWidth
  }),
  mounted () {
    window.addEventListener('resize', this.updateWidth)
  },
  unmounted () {
    window.removeEventListener('resize', this.updateWidth)
  },
  methods: {
    updateWidth () {
      this.width = window.innerWidth
    },
    goToAbout () {
      if (this.$route.name !== 'about') { this.$router.push('/about') }
    },
    goToStore () {
      if (this.$route.name !== 'store') { this.$router.push('/') }
    }
  }
}
</script>

<style>
.logo-icon{
    height: 90%;
}

.logo-img{
    height: 100%;
}
</style>
