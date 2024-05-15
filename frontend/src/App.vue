<template>
  <div id="app">
    <h1>Upload d'une image</h1>
    <div class="upload-container">
      <label for="file-upload" class="custom-file-upload">
        <img src="@/assets/upload-icon.png" alt="Upload Icon" class="upload-icon" />
        <span>Choisir un fichier</span>
      </label>
      <input id="file-upload" type="file" @change="onFileChange" />
    </div>
    <div v-if="imageUrl" class="image-preview">
      <h2>Image uploadée :</h2>
      <img :src="imageUrl" alt="Uploaded Image" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      imageFile: null,
      imageUrl: ''
    };
  },
  methods: {
    async onFileChange(event) {
      this.imageFile = event.target.files[0];
      if (this.imageFile) {
        await this.uploadImage();
      }
    },
    async uploadImage() {
      const formData = new FormData();
      formData.append('image', this.imageFile);

      try {
        const response = await axios.post('http://localhost:3000/upload', formData, {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        });
        this.imageUrl = response.data.imageUrl;
      } catch (error) {
        console.error('Erreur lors du téléchargement de l\'image :', error);
      }
    }
  }
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.upload-container {
  margin-top: 20px;
  margin-bottom: 20px;
  position: relative;
}

.custom-file-upload {
  display: inline-block;
  cursor: pointer;
  border: 2px solid #007bff;
  padding: 10px 20px;
  border-radius: 5px;
  transition: background-color 0.3s;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

.custom-file-upload:hover {
  background-color: #007bff;
  color: white;
}

#file-upload {
  display: none;
}

.upload-icon {
  width: 50px;
  height: 50px;
  vertical-align: middle;
  margin-right: 10px;
}

.image-preview {
  margin-top: 20px;
}

.image-preview img {
  max-width: 100%;
  border-radius: 10px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}
</style>
