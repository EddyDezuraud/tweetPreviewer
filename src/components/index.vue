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
  <div class="appWrapper">
    <Loader v-if="showLoader" @end="onEndLoader" />
    <FormModal v-else-if="showFormModal" @valid="onValidForm" />
    <Tweet v-else-if="showPreviewer" />
  </div>
</template>


<style>
.appWrapper {
  display: flex;
  height: 100vh;
  width: 100%;
  justify-content: space-between;
  flex-direction: column;
  min-height: 100vh;
  padding: 20px;
  box-sizing: border-box;
  gap: 20px;
}

#titlePage {
  text-align: center;
  width: 100%;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: baseline;
  gap: 10px;
}

#titlePage h1 {
  margin: 0;
  padding: 0;
  font-size: 20px;
  line-height: 1;
}

#titlePage>span {
  line-height: 1;
  font-size: 12px;
  font-weight: 700;
}

.twitterLink {
  font-weight: 800;
  font-size: 13px;
}
</style>