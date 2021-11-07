<template>
  <div class="wrapper">

    <div class="content">

      <!--SideMenu template-->
      <SideDrawer v-if="sideMenuOpen"></SideDrawer>

      <!--Navigation panel template-->
      <Navigation :toggleSideMenu="toggleSideMenu"
                  :sideMenuOpen="sideMenuOpen"
                  :toggleModal="toggleModalWindow">

      </Navigation>

    </div>

    <!--Modal window-->
    <ModalWindow v-if="modalOpen"
                 :toggleModal="toggleModalWindow">

    </ModalWindow>

  </div>
</template>

<script>

import ModalWindow from "./components/common/ModalWindow";
import Navigation from "./components/navigation/Navigation";
import SideDrawer from "./components/sideDrawer/SideDrawer";

export default {
  data () {
    return {
      modalOpen: false,
      sideMenuOpen: false,
    }
  },
  components: {
    Navigation: Navigation,
    SideDrawer: SideDrawer,
    ModalWindow: ModalWindow
  },
  methods: {
    toggleSideMenu () {
      this.sideMenuOpen = !this.sideMenuOpen
    },
    toggleModalWindow () {
      this.modalOpen = !this.modalOpen
    },
  }
}
</script>

<style lang="sass">
  *
    margin: 0
    padding: 0

  .content
    display: flex

</style>
