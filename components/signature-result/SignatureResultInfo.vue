<template>
  <div class="signature-result-info">
    <div class="signature-result-info__left">
      <div
        class="signature-result-info__item"
        v-if="$store.state.result.PDF.filename"
      >
        <span
          class="signature-result-info__filename"
          v-if="$store.state.result.PDF.filename"
          ><i></i
          ><span
            >{{ $store.state.result.PDF.filename }}<br /><span
              class="signature-result-info__filename__md5"
              >Контрольная сумма MD5: {{ $store.state.result.PDF.MD5 }}</span
            ></span
          ></span
        >
        <span
          class="signature-result-info__md5"
          v-if="$store.state.result.PDF.MD5"
          >Контрольная сумма MD5: {{ $store.state.result.PDF.MD5 }}</span
        >
      </div>
      <div
        class="signature-result-info__item"
        v-if="$store.state.result.SIG.filename"
      >
        <span
          class="signature-result-info__filename"
          v-if="$store.state.result.SIG.filename"
          ><i></i
          ><span
            >{{ $store.state.result.SIG.filename }}<br /><span
              class="signature-result-info__filename__md5"
              >Контрольная сумма MD5: {{ $store.state.result.SIG.MD5 }}</span
            ></span
          ></span
        >
        <span
          class="signature-result-info__md5"
          v-if="$store.state.result.SIG.MD5"
          >Контрольная сумма MD5: {{ $store.state.result.SIG.MD5 }}</span
        >
      </div>
    </div>
    <div class="signature-result-info__right">
      <button
        class="button button-success button--small"
        @click.prevent="newUpload()"
      >
        Проверить еще
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    newUpload() {
      this.$store.commit("changeResult", {});
      this.$store.commit("changeUploadStatus", "form");
      //this.$router.go(-1);
    }
  }
};
</script>

<style>
.signature-result-info {
  display: flex;
  justify-content: space-between;
  font-size: 0.7rem;
  margin: 20px 40px 25px;
  min-height: 40px;
  height: auto;
}
.signature-result-info__filename {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  max-width: 100%;
}
.signature-result-info__filename i {
  width: 32px;
  height: 32px;
  background: url("~/assets/icon-filename.svg") no-repeat center;
  background-size: contain;
  margin-right: 10px;
}
.signature-result-info__filename > span {
  max-width: calc(100% - 42px);
  word-break: break-word;
}
.signature-result-info__filename__md5 {
  display: none;
  word-wrap: break-word;
}
.signature-result-info__md5 {
  word-wrap: break-word;
}
.signature-result-info__left {
  margin-right: 44px;
  width: calc(100% - 42px);
}
.signature-result-info__item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.signature-result-info .button {
  min-width: 136px;
}
.signature-result-info__again {
  display: none;
}
@media (max-width: 767px) {
  .signature-result-info__right .button {
    display: none;
  }
}
@media (max-width: 575px) {
  .signature-result-info {
    font-size: 0.55rem;
    margin-left: 0;
    margin-right: 0;
  }
  .signature-result-info__md5 {
    display: none;
  }
  .signature-result-info__filename {
    width: 100%;
    margin-right: 0;
  }
  .signature-result-info__filename__md5 {
    display: inline;
  }
}
</style>
