<script setup>
import { ref } from "vue";
const active = ref(false);

const toggleActive = () => {
  active.value = !active.value;
};
</script>

<template>
  <section
    class="drop-zone-container"
    :class="{ 'active-dropzone': active }"
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
  >
    <h2>Drag or Drop file</h2>
    <p>OR</p>
    <label for="dropZoneFile"> Select File </label>
    <input id="dropZoneFile" class="drop-zone-file" type="file" />
  </section>
</template>

<style scoped lang="scss">
.drop-zone-container {
  width: 100%;
  height: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  border: 2px dashed #41b883;
  background-color: #fff;
  transition: all 0.3s ease;

  label {
    padding: 8px 12px;
    color: #fff;
    background-color: #41b883;
    transition: all 0.3s ease;
  }

  input {
    display: none;
  }
}

.active-dropzone {
  background-color: #41b883;
  border-color: #fff;
  color: #fff;

  label {
    background-color: #fff;
    color: #41b883;
  }
}
</style>