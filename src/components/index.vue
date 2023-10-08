<script setup>
import Loader from './Loader.vue';
import FormModal from './FormModal.vue';
import Tweet from './Tweet.vue';
import { ref } from 'vue';

const usernameId = ref('');
const username = ref('');
const showLoader = ref(true);
const showFormModal = ref(false);
const showPreviewer = ref(false)

const onEndLoader = () => {
  console.log('end')
  showLoader.value = false;
  showFormModal.value = true;
}

const onValidForm = (e) => {
  usernameId.value = e.username;

  showFormModal.value = false;
  showPreviewer.value = true;
}

</script>

<template>
  <div :class="$style.wrapper">
    <Loader v-if="showLoader" @end="onEndLoader" />
    <FormModal v-else-if="showFormModal" @valid="onValidForm" />
    <div :class="$style.tweetPage" v-else-if="showPreviewer" >
      <Tweet :username="usernameId"/>
    </div>
  </div>
</template>

<style module>
.wrapper {
  width: 100%;
  height: 100%;
}

.tweetPage {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
}
</style>