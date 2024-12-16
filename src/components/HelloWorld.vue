<template>
  <div class="hello">
    <button class="btn green" @click="show">Fade Modal</button>
  </div>
</template>

<script>
import DynamicModal from './DynamicModal.vue';
export default {
  name: 'HelloWorld',
  components: {
    DynamicModal
  },
  props: {
    msg: String
  },
  methods: {
    show() {
      this.$modal.show(DynamicModal, {
        overlayTransition: 'vm-transition--overlay',
        transition: "vm-transition--modal"
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button.btn.green {
    box-shadow: 0 4px 8px rgba(80, 201, 186, .3);
    background: #50c9ba;
}
button.btn {
    outline: none;
    background: #fff;
    border: 0;
    padding: 10px 18px;
    cursor: pointer;
    color: #fff;
    box-shadow: 0 4px 8px rgba(32, 160, 255, .3);
    background: #4db3ff;
    font-weight: 600;
    border-radius: 3px;
    min-width: 90px;
    margin-bottom: 8px;
    margin-top: 8px;
    margin-right: 8px;
}
</style>
