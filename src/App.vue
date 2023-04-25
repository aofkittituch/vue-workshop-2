<template>
  <div id="">
    <div class="container">
      <h2>Workshop #2 - Preview Image</h2>
      <hr />
      <div v-if="!url">
        <input type="file" class="form-control" @change="onFileChange" />
        <hr />
      </div>
      <div id="preview" v-else>
        <img :src="url" />
        <button class="btn btn-danger" @click="removeImage">
          Delete Image
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return { url: null };
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file);
    },
    removeImage() {
      this.url = null;
    },
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
}

#preview {
  display: flex;
  justify-content: center;
  align-items: center;
}

#preview img {
  max-width: 100%;
  max-height: 500px;
}
</style>
