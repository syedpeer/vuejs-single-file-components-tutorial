<template lang="pug">
div
  h1 Welcome!
  p Hello, {{name}}
</template>

<script>
module.exports = {
  data: function () {
    return {
      name: 'Sam'
    }
  }
}
</script>

<style lang="sass" scoped>

  $primary-colour: #33c689;
  $letting-spacing: 3px;

  p
    text-align: center;
    color: $primary-colour;
    letter-spacing: $letting-spacing;
</style>
