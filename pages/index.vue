<template>
  <div class="container" id="container">
    <div class="instructions">Hello from this side
      <p>Here's the code this guy just wrote {{ code }}</p>
      <button @click="test">Click me</button>
    </div>
    <div id="app" class="editor"></div>
  </div>
</template>

<script>
export default {
  data: () => ({
    options: {
      autoIndent: 'full',
      tabSize: 2,
      theme: 'vs-dark',
      language: 'javascript'
    },
    code: ''
  }),
  mounted () {
    const _this = this;
    const monaco = require('monaco-editor');
    monaco.editor.create(document.getElementById('app'), _this.options);
  },
  methods: {
    test () {
      const monaco = require('monaco-editor');
      this.code = monaco.editor.getModels()[0].getValue();
      console.log(this.code);
    }
  },
  watch: {
    value (value) {
      console.log(value);
    }
  }
};
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: center;
  .instructions {
    height: 100%;
    flex: 0 0 45%;
  }
  .editor {
    flex: 0 0 45%;
    width: 100%;
    height: calc(100vh - 80px);
    text-align: left
  }
}

</style>
