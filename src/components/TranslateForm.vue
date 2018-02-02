<template>
    <div class="row" id="translateForm">
        <div class="col-md-offset-3 col-md-6">
            <form class="form-inline well" @submit="formSubmit">
                <input  class="form-control" type="text" placeholder="输入需要翻译的内容" v-model="content">
                <select class="form-control" v-model="language">
                    <option value="en">English</option>
                    <option value="ru">Russian</option>
                    <option value="ko">Korean</option>
                    <option value="ja">Janpenese</option>
                </select>
                <input class="form-control btn btn-primary" type="submit" value="翻译">
            </form>
        </div>
    </div>
</template>

<script>
    
    export default {
        name: "translateForm",
        data() {
          return {
              content: '',
              language: ''
          }
        },
        methods: {
            formSubmit: function (e) {
                this.$emit('formSubmit', this.content, this.language);
                e.preventDefault();
            }
        },
        created: function () {
            this.language = 'en'
        }
    }
    
</script>

<style scoped>

</style>