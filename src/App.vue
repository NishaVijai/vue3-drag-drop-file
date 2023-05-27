<template>
  <h1>DropZone</h1>
  <DropZone @drop.prevent="drop" @change="selectedFile" />
  <p class="file-info">
    {{ dropzoneFile ? "Selected File - " : "Please select a file" }}
    {{ dropzoneFile.name }}
  </p>
</template>

<script>
import DropZone from "./components/DropZone.vue";
import { ref } from "vue";

export default {
  name: "App",
  components: {
    DropZone,
  },
  setup() {
    let dropzoneFile = ref("");

    const drop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0];
    };

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".drop-zone-file").files[0];
    };

    return {
      dropzoneFile,
      drop,
      selectedFile,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  background-color: rgb(237, 241, 241);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.file-info {
  margin-top: 1rem;
}

.open-selected-file {
  display: none;
}
</style>
