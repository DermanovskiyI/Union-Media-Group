<template>
    <div class="wrapper">
        <div class="user">Вася</div>
        <user-list/>
    </div>
</template>

<script>
import userList from '../components/UserList.vue';

export default {
  components: {
    userList,
  },
  data() {
    return {
      user: [{
        id: 1,
        name: 'Вася',
      }, {
        id: 2,
        name: 'Петя',
      }], // В массиве может быть от 2 пользователей, все с уникальными id > 0
      selectUser: 0, // id выбранного пользователя. 0 если не выбрано
    };
  },
};
</script>

<style lang="scss">
.user {
    margin-bottom: 20px;
    text-align: center;
}
</style>
