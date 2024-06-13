<template>
  <form action="#" @submit.prevent="onSubmit">
    <p v-if="errorsPresent" class="error">Please fill out all fields!</p>

    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="germany flag"></i> German
      </div>
      <input type="text" placeholder="Enter word in German..." v-model="word.german" />
    </div>

    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="united kingdom flag"></i> English
      </div>
      <input type="text" placeholder="Enter word in English..." v-model="word.english" />
    </div>

    <!-- Urdu input field added below -->
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="pakistan flag"></i> Urdu
      </div>
      <input type="text" placeholder="Enter word in Urdu..." v-model="word.urdu" />
    </div>
    <!-- Urdu input field ends here -->

    <button class="positive ui button">Submit</button>
  </form>
</template>

<script>
export default {
  name: 'word-form',
  props: {
    word: {
      type: Object,
      required: false,
      default: () => ({
        english: '',
        german: '',
        urdu: '', // Initialize Urdu property
      }),
    },
  },
  data() {
    return {
      errorsPresent: false
    };
  },
  methods: {
    onSubmit: function() {
      if (this.word.english === '' || this.word.german === '' || this.word.urdu === '') {
        this.errorsPresent = true;
      } else {
        this.$emit('createOrUpdate', this.word);
        this.errorsPresent = false;
      }
    }
  }
};
</script>

<style scoped>
.error {
  color: red;
}
</style>
