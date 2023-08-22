<template>
  <h1>{{ hello_msg }}</h1>
  <!-- <div>
    <input ref="hello"/>
  </div> -->
  <button class="toggleButton" @click="toggleModal">toggle modal</button>
  <button class="toggleButton button-2" @click="toogleModalTwo">toggle modal two</button>
  <div v-if="showModal">
    <MyModal :type="type" @close-modal="toggleModal">
      <h1>Hello World!</h1>
      <template v-slot:links>
        <a class="link-button" href="#">sign up</a>
        <a class="link-button" href="#">more info</a>
      </template>
    </MyModal>
  </div>

  <div v-if="showModalTwo">
    <MyModal :header="model_header" @close-modal="toogleModalTwo">
      <h1>
        This is second modal.
      </h1>
      <template v-slot:links>
        <a class="link-button">
            register
        </a>
      </template>
    </MyModal>
  </div>

</template>

<script>
import MyModal from "./components/MyModal.vue"


export default {
  name: 'App',
  components: {MyModal},
  data() {
    return {
      hello_msg: "This is hello message.",
      model_header: "This is props model header.",
      type: "success",
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toogleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100%;
}
.toggleButton{
  margin: 0 5px;
  padding: 10px 15px;
  font-size: 16px;
}
.link-button{
  margin: 0 5px;
  padding: 8px 15px;
  background: rgba(0, 0, 0, 0.3);
  color: white;
}
.link-button:hover{
  background: rgba(0, 0, 0, 0.4);
}
</style>
