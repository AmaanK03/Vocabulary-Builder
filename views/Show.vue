<template>
  <div>
    <h1>Show Word</h1>

    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="germany flag"></i> German
      </div>
      <input type="text" readonly :value="word.german"/>
    </div>

    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="united kingdom flag"></i> English
      </div>
      <input type="text" readonly :value="word.english"/>
    </div>
<!-- Urdu input field ends here -->
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="pakistan flag"></i> 

        Urdu
      </div>
      <input type="text" readonly :value="word.urdu"/>
    </div>
    <!-- Urdu input field ends here -->
    
    <div class="actions">
      <router-link :to="{ name: 'edit', params: { id: this.$route.params.id }}">
        Edit word
      </router-link>
    </div>
  </div>
</template>

<script>
import { api } from '../helpers/helpers';

export default {
name: 'show',
data() {
  return {
    word: {
      german: '',
      english: '',
      urdu: '' // Initialize Urdu property
    }
  };
},
async mounted(){
  this.word = await api.getWord(this.$route.params.id);
}
};
</script>

<style scoped>
.actions a {
display: block;
text-decoration: underline;
margin: 20px 10px;
}
</style>
