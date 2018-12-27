<template>
  <div class="main">
      <div class="main__container" :class="{ blur: blur }">
        <Header @open-modal="openMod"></Header>
            <Menu>
            </Menu>
    </div>
      <Modal v-show="showModal" @closeModal="closeMod"/>
  </div>
</template>

<script>
import Menu from './menu'
import Header from './header'
import Modal from './modal'
export default {
  name: "Main",
  data() {
    return {
      showModal: false,
      blur: false,
      showMenu: false,
      menuOpened: false
    };
  },
  methods: {
    openMod: function() {
      this.showModal = true;
      this.blur = true;
    },
    closeMod: function(event) {
        this.showModal = false;
        this.blur = false;
    }
  },
  components: {
    Menu,
    Modal,
    Header
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.fade-enter-active, .fade-leave-active {
    transition: all .4s;
}
.fade-enter, .fade-leave-to {
    transform: translateY(-100%);
}
.fade-leave, .fade-enter-to {
    transform: translateY(0);
}
.blur {
  filter: blur(4px);
}
.main {
  background-color: rgba(255,255,255,0.5);
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: row;
  position: relative;
}
.main__container {
  width: 100vw;
  height: 100vh;
}
</style>
