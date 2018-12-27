<template>
  <div class="menu-section">
        <div class="spans" @click="rotate">
          <div :class="{first: !active, rotated: active}"></div>
          <div :class="{pos: !active, disappeared: active}"></div>
          <div :class="{last: !active, rotatedReversed: active}"></div>
        </div>
        <ul id="list">
            <li v-for="li in lis" :key="li.index" @mouseover="scalePlus($event)" @mouseout="scaleMinus($event)">
              <transition name="fade">
                <div v-show="active"><p class="not__active"> {{li.msg}} </p></div>
              </transition>
              <img :src="li.icon" alt="">
            </li>
        </ul>
  </div>
</template>

<script>
export default {
  name: "Menu",
  data() {
    return {
      active: true,
      lis: {
        1: {
          msg: 'Главная',
          index: 1,
          icon: require('../assets/home.svg')
        },
        2: {
          msg: 'О проекте',
          index: 2,
          icon: require('../assets/information.svg')
        },
        3: {
          msg: 'Как это работает',
          index: 3,
          icon: require('../assets/focus.svg')
        },
        4: {
          msg: 'Наша команда',
          index: 4,
          icon: require('../assets/about-us.svg')
        },
        5: {
          msg: 'Сотрудничество',
          index: 5,
          icon: require('../assets/hand-shake.svg')
        },
        6: {
          msg: 'Контакты',
          index: 6,
          icon: require('../assets/contact.svg')
        }
      }
    };
  },
  methods: {
    scalePlus(e) {
      e.currentTarget.querySelector('div > p').classList.add('active');
      e.currentTarget.querySelector('div > p').classList.remove('not__active');
    },
    scaleMinus(e) {
      e.currentTarget.querySelector('div > p').classList.remove('active');
      e.currentTarget.querySelector('div > p').classList.add('not__active');
    },
    rotate(e) {
      this.active = !this.active;
    }
  },
  created() {
    
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  color: black;
}
.fade-enter-active, .fade-leave-active {
  transition: 0.5s all;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.fade-enter-to, .fade-leave {
  opacity: 1;
}
.active {
  color: black;
  transform: translateX(-5px);
}
.menu-section {
  position: absolute;
  width: 80px;
  min-height: 500px;
  background-color: #344055;
  top: 50%;
  transform: translateY(-50%);
  right: 25px;
  border-radius: 150px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0px 2px 31px -4px rgba(0,0,0,0.3);
}
.spans {
  width: 100%;
  height: 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  position: relative;
}
.spans > div {
  width: 30px;
  height: 1px;
  background-color: white;
  transition: 0.5s;
  position: absolute;
}
.first {
  transform: translateY(-6px);
}
.last {
  transform: translateY(6px);
}
.rotated {
  transform: rotate(-45deg);
}
.rotatedReversed {
  transform: rotate(45deg);
}
.disappeared {
  opacity: 0;
  position: absolute;
}
#list {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: right;
}
#list > li {
  display: flex;
  padding: 10px;
  flex-direction: row;
  align-items: center;
  width: 100%;
  justify-content: center;
  cursor: pointer;
  position: relative;
  padding: 15px;
}
#list img {
  width: 25px;
  height: 25px;
}
#list div {
  position: absolute;
  font-family: 'Source Sans Pro', sans-serif;
  top: 0;
  z-index: 99;
  font-size: 1rem;
  top: 50%;
  display: flex;
  justify-content: flex-end;
  width: 100%;
  text-align: right;
  align-items: flex-end;
  transform: translateY(-50%);
  left: -90px;
}

#list p {
   transition: 0.3s;
}
.not__active {
  color: rgba(0,0,0,.7);
}
</style>