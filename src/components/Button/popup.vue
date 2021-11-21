<template>
 <div class="popup" v-if="showPopup" @click="hidePopup">
   <div class="popup__content" @click.stop="this.showPopup=true">
       <header>
           <h2 class="popup__title">Invalid Input</h2>
       </header>
       <div class="popup__para">
            <p class="popup__des">Unfortunately, at least one input value is invalid.</p>
            <p class="popup__des">Please check all inputs and make sure you enter at least a few characters into each input field.</p>
        </div>
        <div class="popup__btn">
            <button @click.stop="hidePopup">Okay</button>
        </div>
   </div>
   
 </div>
  
</template>

<script>

export default {
  name: 'popup',
  components: {
    
  },
  props: {
     
  },
  data() {
      return {

      }
  },
  methods: {
    hidePopup() {
        this.showPopup = false;
    }
  }
}
</script>

<style scoped>
.popup {
    position: fixed;
    width: 100%;
    height: 100vh;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.5)
}
.popup__content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 40%;
    border-radius: 15px;
    background-color: #fff;
    overflow: hidden;
}
.popup__title {
    font-size: 1.5rem;
    color: #FFF;
    font-weight: bold;
    background-color: #3a0061;
    padding: 1rem;
    font-family: 'Roboto', sans-serif;
}
.popup__para {
    padding: 1rem;
}
.popup__des {
    font-family: 'Roboto', sans-serif;
    font-style: normal;
    font-size: 1.2rem;
    padding: 0.5rem 0;
    line-height: 1.2;
    color: #000;
}
.popup__btn {
    padding: 1rem;
    display: flex;
    justify-content: flex-end;
    margin: 0;
}
.popup__btn button {
    font-size: 1rem;
    padding: 0.75rem;
    font-family: inherit;
    color: #FFF;
    border: none;
    outline: none;
    cursor: pointer;
    border: 1px solid transparent;
    transition: all 0.5s;
    border-radius: 10px;
    background-color: #3a0061;
}
.popup__btn button:hover {
    background-color: #270041;
}
</style>
