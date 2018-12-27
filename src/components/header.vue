<template>
  <div class="header__section">
    <div class="header">
        <div class="buttons">
            <div class="sign-in__button" @click="$emit('open-modal')"><p>Войти</p></div>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Header",
  data() {
      return {
        
      }
  },
  methods: {
      
   }
};
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
.header__section {
    width: 100%;
    padding: 25px;
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
}
.sign-in__button {
    color: black;
    padding: 15px;
    cursor: pointer;
    width: 100px;
    height: 50px;
    border-radius: 10px;
    border: 1px solid rgba(0,0,0,0.7);
    transition: 0.3s;
}
.sign-in__button:hover {
    transform: scale(1.05,1.05);
    border: 1px solid black;
}
</style>
