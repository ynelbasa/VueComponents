<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div
        class="modal"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header class="modal-header" id="modalTitle">
          <slot name="header">
            {{title}}
            <img
              src="./../assets/close.svg"
              width="20px"
              class="btn-close"
              @click="close"
              aria-label="Close modal"
            />
          </slot>
        </header>
        <section class="modal-body" id="modalDescription">
          <div class="icon">
            <img src="./../assets/info.svg" style="width: 60px" v-if="type==='info'" />
            <img src="./../assets/warning.svg" style="width: 60px" v-if="type==='warning'" />
            <img src="./../assets/confirm.svg" style="width: 60px" v-if="type==='confirmation'" />
          </div>
          <div class="text">
            <slot name="body">{{message}}</slot>
          </div>
        </section>
        <footer class="modal-footer">
          <slot name="footer">
            <v-button text="close" type="rounded" @click="close" v-if="type==='info'"></v-button>
            <v-button text="ok" type="rounded" @click="close" v-if="type==='warning'"></v-button>
            <v-button
              text="disagree"
              type="text"
              color="#ff1919"
              @click="close"
              v-if="type==='confirmation'"
            ></v-button>
            <v-button text="agree" type="rounded" @click="close" v-if="type==='confirmation'"></v-button>
          </slot>
        </footer>
      </div>
    </div>
  </transition>
</template>

<script>
import Button from "./Button";

export default {
  name: "v-dialog",
  props: {
    title: { type: String, default: "Default Title" },
    message: { type: String, default: "Default Body Text" },
    type: { type: String, default: "info" }, // values: info, warning, confirmation
  },
  components: { "v-button": Button },
  methods: {
    close() {
      this.$emit("close");
    },
  },
  computed: {
    isConfirmation: function () {
      return this.type === "confirmation";
    },
  },
};
</script>

<style scoped>
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}

.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  border-radius: 4px;
  max-width: 320px;
}

.modal-header,
.modal-footer {
  display: flex;
}

.modal-header {
  padding: 15px;
  font-size: 12pt;
  border-bottom: 1px solid #eeeeee;
  color: white;
  background-color: #42b983;
  justify-content: space-between;
}

.modal-footer {
  padding: 5px;
  border-top: 1px solid #eeeeee;
  justify-content: center;
  margin: 5px;
}

.modal-body {
  font-size: 10pt;
  position: relative;
  padding: 20px 10px;
  display: flex;
}

.modal-body .icon {
  display: inline-block;
}

.modal-body .text {
  display: inline-block;
}

.btn-close {
  cursor: pointer;
}
</style>
