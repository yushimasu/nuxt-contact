<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">nuxt-contact</h1>
      <div class="p-contact">
        <validation-observer
          ref="observer"
          v-slot="{ invalid, validated }"
          tag="form"
          class="p-contact__form"
          name="contact"
          method="POST"
          data-netlify="true"
          data-netlify-honeypot="bot-field"
          @submit.prevent="onSubmit"
          :class="sendingClass"
        >
          <input type="hidden" name="form-name" value="contact" />

          <div class="p-contact__item">
            <label for="username">お名前</label>
            <validation-provider
              v-slot="{ errors }"
              rules="required|max:100"
              name="お名前"
              mode="lazy"
            >
              <input
                type="text"
                id="username"
                name="username"
                v-model="username"
                autocomplete="name"
              />
              <p v-show="errors.length" class="p-contact__error">
                {{ errors[0] }}
              </p>
            </validation-provider>
          </div>
          <!-- /.p-contact__item -->

          <div class="p-contact__item">
            <label for="katakana">フリガナ</label>
            <validation-provider
              v-slot="{ errors }"
              rules="required|katakana"
              name="フリガナ"
            >
              <input
                type="text"
                id="katakana"
                name="katakana"
                v-model="katakana"
              />
              <p v-show="errors.length" class="p-contact__error">
                {{ errors[0] }}
              </p>
            </validation-provider>
          </div>
          <!-- /.p-contact__item -->

          <div class="p-contact__item">
            <label for="useremail">メールアドレス</label>
            <validation-provider
              v-slot="{ errors }"
              rules="required|email|max:256"
              name="メールアドレス"
            >
              <input
                type="text"
                id="useremail"
                name="useremail"
                v-model="useremail"
                autocomplete="email"
              />
              <p v-show="errors.length" class="p-contact__error">
                {{ errors[0] }}
              </p>
            </validation-provider>
          </div>
          <!-- /.p-contact__item -->

          <div class="p-contact__item">
            <label for="message">お問い合わせ内容</label>
            <validation-provider
              v-slot="{ errors }"
              rules="required|max:1000"
              name="お問い合わせ内容"
            >
              <textarea
                id="message"
                name="message"
                v-model="message"
              ></textarea>
              <p v-show="errors.length" class="p-contact__error">
                {{ errors[0] }}
              </p>
            </validation-provider>
          </div>
          <!-- /.p-contact__item -->

          <div class="p-contact__item" v-show="false">
            <label for="message">スパムでない場合は空欄</label>
            <input type="text" name="bot-field" v-model="botField" />
          </div>
          <!-- /.p-contact__item -->

          <div class="p-contact__submit">
            <button type="submit" :disabled="invalid || !validated">
              送信
            </button>
          </div>
          <!-- /.p-contact__submit -->
        </validation-observer>
        <!-- /.p-contact__form -->
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
.p-contact__error{
  color: #ff0111;
}
</style>
