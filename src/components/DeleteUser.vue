<template>
  <user-alert v-if="alertIsVisible" :title="alertTitle" @close="hideAlert">
    <p>Do you want to continue with deleting a user?</p>
  </user-alert>
  <section>
    <h2>Delete a User</h2>
    <button @click="showAlert">Delete User</button>
  </section>
</template>

<script>
import { ref } from 'vue';
import UserAlert from '../components/UserAlert.vue';
import useAlert from '../hooks/alert';
// import alertMixin from '../mixins/alert';

export default {
  components: {
    UserAlert
  },
  // data() {
  //   return {
  //     alertTitle: 'delete user?'
  //   };
  // },
  // component 안에 data 프로퍼티가 있고, mixin 안에도 같은 data 프로퍼티가 있는 경우,
  // component 안의 data 프로퍼티에 merge 된다. 즉, 같은 이름의 프로퍼티는,
  // component 안에 data 프로퍼티 값으로 적용됌.
  // mixins: [alertMixin],
  setup() {
    const alertTitle = ref('Delete User?');

    const [alertIsVisible, showAlert, hideAlert] = useAlert(true);

    return { alertTitle, alertIsVisible, showAlert, hideAlert };
  }
};
</script>
