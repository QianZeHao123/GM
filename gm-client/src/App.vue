
<template>
  <div class="mockup-browser border border-base-300">
    <div class="mockup-browser-toolbar">
      <div class="input border border-base-300">Data Visualization</div>
    </div>
    <div class="flex justify-center px-4 py-16 border-t border-base-300">
      <ChallengeOne />
    </div>
  </div>

  <!-- <div>Data Visualization</div>
  <ChallengeOne /> -->
</template>


<script>
// import HelloWorld from './components/HelloWorld.vue'
import ChallengeOne from './components/Challenge1.vue';
export default {
  name: "App",
  components: {
    ChallengeOne,
  },
  data() {
    return {}
  },
  methods: {},
  mounted() { },
}
</script>



<style scoped></style>



