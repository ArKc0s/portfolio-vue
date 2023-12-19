<template>
  <div>
    <div class="title">Hey ! I'm Léo WADIN,</div>
    <div class="title inline-flex gap-3">
      Currently
      <WritingText
        :phrases="[
          'web developer',
          'UI Designer',
          'software engineer',
          'esport team CEO',
          'apprentice',
        ]"
      />
    </div>
  </div>
</template>

<style lang="scss">
.title {
  color: white;
  font-size: 4rem;
  font-weight: 700;
}
</style>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import WritingText from '@/components/WritingText.vue';

@Options({
  components: {
    WritingText,
  },
})
export default class HomeView extends Vue {}
</script>
