<script setup>
import Loader from './Loader.vue'
import FormModal from './FormModal.vue';
import Tweet from './Tweet.vue';
import { ref } from 'vue';

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
  username.value = e.username;
}

</script>

<template>
  <div>
    <Loader v-if="showLoader" @end="onEndLoader" />
    <FormModal v-else-if="showFormModal" @valid="onValidForm" />
    <Tweet v-else-if="showPreviewer" />
  </div>
</template>