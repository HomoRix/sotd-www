<template>
  <div class="item">
    <p class="heading">Icon</p>
    <div class="file-upload">
      <BaseFileUpload
        :resize-width="192"
        message="<span class=dropzone-plus><img width=150 src=/images/sample-icon.png></span><br>Drop your icon here, or click to select"
        @uploadSuccess="setIcon"
        @removeFile="removeIcon"/>
    </div>
    <p class="help">Dimensions must be 192px width by 192px height <br>(JPEG or PNG format) <br><a 
      href="https://cm-dapp-store.oss-cn-beijing.aliyuncs.com/common/image_guidelines_08152018.png"
      target="_blank">View the guidelines/examples</a></p>
  </div>
</template>

<script>
import BaseFileUpload from '~/components/BaseFileUpload'

export default {
  components: {
    BaseFileUpload
  },
  methods: {
    setIcon(reponse) {
      const field = {
        name: 'iconUrl',
        value: reponse.url || ''
      }
      this.$store.dispatch('dapps/form/setField', field)
    },
    removeIcon() {
      const field = {
        name: 'iconUrl',
        value: ''
      }
      this.$store.dispatch('dapps/form/setField', field)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/css/settings';

.file-upload {
  box-shadow: 0 0 20px rgba($color--black, 0.05);
}
</style>
