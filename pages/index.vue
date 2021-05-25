<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">nuxt-contact</h1>
      <form name="contact" method="POST" data-netlify="true">
        <input type="hidden" name="form-name" value="contact">
        <p>
          <label>お名前<input type="text" name="name" /></label>
        </p>
        <p>
          <label>メールアドレス<input type="email" name="email" /></label>
        </p>
        <p>
          <label
            >体調
            <select name="role[]" multiple>
              <option value="元気">元気</option>
              <option value="よくない">よくない</option>
            </select></label
          >
        </p>
        <p>
          <label>備考<textarea name="message"></textarea></label>
        </p>
        <p>
          <button type="submit">送信</button>
        </p>
      </form>
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
</style>
