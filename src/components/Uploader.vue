<template>
  <div>
    <q-modal ref="uploader" class="uploader" :content-css="{padding: '50px', minWidth: '50vw', minHeight: '80vh'}">
      <div class="modal-header" v-html="'Upload images'"></div>
      <div class="modal-body modal-scroll" v-html="'Choose the images you want to upload'"></div>
      <div class="modal-body modal-scroll">
        <q-uploader :additionalFields="additionalUploadFields" url="http://localhost:3000/image-upload" multiple extensions=".jpg, .jpeg" hide-upload-progress color="primary" class="col-6" />
      </div>
    </q-modal>
    <div class="layout-padding row items-start">
      <q-btn icon="file upload" small flat color="primary" @click="uploadFiles">
        Upload File
      </q-btn>
    </div>
  </div>
</template>

<script>
import { QBtn, QModal, QUploader } from 'quasar-framework'
export default {
  components: { QBtn, QModal, QUploader },
  data () {
    return {
      foldername: 'uploadTo'
    }
  },
  computed: {
    additionalUploadFields () {
      return [{ name: 'foldername', value: this.folderName }]
    }
  },
  methods: {
    uploadFiles () {
      this.$refs.uploader.open()
    }
  }
}
</script>

<style>
.q-uploader .q-input-target {
  padding-left: 10px;
}

.q-uploader .q-uploader-progress-text {
  font-size: 16px;
}

.q-uploader-progress-bg {
  height: 4px;
  opacity: 0.9;
}
</style>
