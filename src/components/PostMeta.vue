<template>
  <div class="post-meta">
    <strong>
      {{ post.author }}
    </strong>
    <br />
    <small>
      Publicado {{ post.date }}.
      <br />
      <template v-if="post.timeToRead">
        <strong>Tiempo de lectura: {{ post.timeToRead }} min.</strong>
      </template>
    </small>
  </div>
</template>

<script>
export default {
  props: ["post"],
};
</script>

<style lang="scss">
.post-meta {
  font-size: 0.8em;
  opacity: 0.8;
}
</style>
