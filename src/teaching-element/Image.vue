<template>
  <retouch-transformer :width="400" :height="400" fit="inside">
    <retouch-transformer :width="400" :height="300" crop>
      <retouch-image
        v-bind="meta"
        :service-url="serviceUrl"
        :name="name"
        :placeholder="placeholder"
        prefetch
        class="te-image" />
    </retouch-transformer>
  </retouch-transformer>
</template>

<script>
import { RetouchImage, RetouchTransformer } from 'vue-retouch';

export default {
  name: 'te-image',
  props: {
    name: { type: String, required: true },
    placeholder: { type: String, default: null },
    meta: { type: Object, default: () => ({}) }
  },
  data: () => ({ serviceUrl: 'http://localhost:3300/api/v1/images/' }),
  components: {
    RetouchImage,
    RetouchTransformer
  }
};
</script>

<style lang="scss">
.te-image img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 0 auto;
}
</style>
