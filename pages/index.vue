<template>
  <div class="index-page-content">
    <signature-result
      v-if="
        $store.state.uploadStatus === 'success' &&
          $store.state.result.signatures
      "
    ></signature-result>

    <signature-error
      v-else-if="$store.state.uploadStatus === 'error'"
    ></signature-error>

    <upload-form v-else></upload-form>
  </div>
</template>

<script>
import UploadForm from "../components/upload-form/UploadForm.vue";
import SignatureResult from "../components/signature-result/SignatureResult.vue";
import SignatureError from "../components/SignatureError.vue";

export default {
  components: {
    UploadForm,
    SignatureError,
    SignatureResult
  },
  layout: "default",
  mounted() {
    //browser history
    window.onpopstate = event => {
      if (
        this.$router.history.current.name === "index" &&
        this.$router.history.current.hash === ""
      ) {
        this.$store.commit("changeResult", {});
        this.$store.commit("changeUploadStatus", "form");
      }
    };
  }
};
</script>
