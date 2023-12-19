<template>
  <div class="writing-text">{{ currentText }}</div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
@Options({
  props: {
    phrases: Array,
  },
})
export default class WritingText extends Vue {
  phrases!: Array<string>;

  currentText = '';
  currentPhraseIndex = 0;
  isDeleting = false;
  typingSpeed = 150; // ms

  created() {
    this.typePhrase();
  }

  typePhrase() {
    const currentPhrase = this.phrases[this.currentPhraseIndex];

    if (this.isDeleting) {
      this.currentText = currentPhrase.substring(
        0,
        this.currentText.length - 1
      );
    } else {
      this.currentText = currentPhrase.substring(
        0,
        this.currentText.length + 1
      );
    }
    let timeout = this.typingSpeed;

    if (!this.isDeleting && this.currentText === currentPhrase) {
      timeout = 2000; // Pause à la fin avant de commencer à effacer
      this.isDeleting = true;
    } else if (this.isDeleting && this.currentText === '') {
      this.isDeleting = false;
      this.currentPhraseIndex =
        (this.currentPhraseIndex + 1) % this.phrases.length;
      timeout = 500; // Pause à la fin de l'effacement
    }

    setTimeout(() => this.typePhrase(), timeout);
  }
}
</script>

<style scoped lang="scss">
.writing-text {
  color: #8695dc;
}
</style>
