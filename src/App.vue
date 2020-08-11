<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h2>Vue.js Components</h2>
    <div>
      <h3>Button Size</h3>
      <v-button text="xsmall" size="xsmall"></v-button>
      <v-button text="small" size="small"></v-button>
      <v-button text="default" size="default"></v-button>
      <v-button text="large" size="large"></v-button>
      <v-button text="xlarge" size="xlarge"></v-button>
    </div>
    <div>
      <h3>Button Type</h3>
      <v-button text="normal" type="normal"></v-button>
      <v-button text="outlined" type="outlined"></v-button>
      <v-button text="rounded" type="rounded"></v-button>
      <v-button text="tile" type="tile"></v-button>
      <v-button text="text" type="text"></v-button>
    </div>
    <div>
      <h3>Dialog Type</h3>
      <v-dialog
        v-show="showInfoDialog"
        @close="closeInfoDialog"
        title="Vue Component - Information"
        message="Components are reusable Vue instances with a name. To find more information follow and subscribe to Vue.js Documentation. "
        type="info"
      ></v-dialog>
      <v-dialog
        v-show="showWarningDialog"
        @close="closeWarningDialog"
        title="Vue Component - Warning"
        message="Components are reusable Vue instances with a name. To find more information follow and subscribe to Vue.js Documentation. "
        type="warning"
      ></v-dialog>
      <v-dialog
        v-show="showConfirmDialog"
        @close="closeConfirmDialog"
        title="Vue Component - Confirmation"
        message="Components are reusable Vue instances with a name. To find more information follow and subscribe to Vue.js Documentation. "
        type="confirmation"
      ></v-dialog>

      <v-button text="info" type="rounded" @click="openInfoDialog"></v-button>
      <v-button text="warning" type="rounded" color="orange" @click="openWarningDialog"></v-button>
      <v-button text="confirmation" type="rounded" color="#1867c0" @click="openConfirmDialog"></v-button>
    </div>
  </div>
</template>

<script>
import Dialog from "./components/Dialog";
import Button from "./components/Button";

export default {
  name: "App",
  components: {
    "v-dialog": Dialog,
    "v-button": Button,
  },
  data() {
    return {
      showInfoDialog: false,
      showWarningDialog: false,
      showConfirmDialog: false,
      dialogType: "",
    };
  },
  methods: {
    openInfoDialog() {
      this.showInfoDialog = true;
    },
    openWarningDialog() {
      this.showWarningDialog = true;
    },
    openConfirmDialog() {
      this.showConfirmDialog = true;
    },
    closeInfoDialog() {
      this.showInfoDialog = false;
    },
    closeWarningDialog() {
      this.showWarningDialog = false;
    },
    closeConfirmDialog() {
      this.showConfirmDialog = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h3 {
  padding-right: 15px;
  display: inline-block;
}
</style>
