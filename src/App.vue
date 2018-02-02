<template>
  <div class="container" id="app">
      <h1>在线翻译</h1>
      <h5 class="text-muted">简单 / 易用 / 便捷</h5>
      <translateForm v-on:formSubmit="translateText"></translateForm>
      <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
    data() {
      return {
          translatedText: ''
      }
    },
  components: {
      TranslateForm,
      TranslateOutput
  },
    methods: {
        translateText: function ( text, language) {
            //alert(text);
            this.$http.get("https://translate.yandex.net/api/" +
                "v1.5/tr.json/translate?key=trnsl.1.1.20180202T0" +
                "15657Z.ce500d8839dd8dd4.de211850caa7ea66c9051ed" +
                "59a2931ea2bb09578&lang=" + language + "&text=" + text)
                .then((response) => {
                    this.translatedText = response.body.text[0];
            })
        }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
