<template>
    <div class="wrapper">
        <div class="user">
            <div class="user__selected" v-if="selectedUser">
                <div class="user__name">{{selectedUser.name}}</div>
                <div class="user__id">{{selectedUser.id}}</div>
            </div>
            <ul class="user__not-selected">
                <li class="user__not-selected-item" v-for="user in notSelectedUsers" :key="user.id">
                    <div class="user__name">{{user.name}}</div>
                    <div class="user__id">{{user.id}}</div>
                </li>
            </ul>
        </div>
        <user-list
            :users="user"
            :selectUser="selectUser"
            @handleSelect="handleSelect"
        />
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
      }, {
        id: 3,
        name: 'Виталий',
      }, {
        id: 4,
        name: 'Семен',
      }],
      selectUser: 0,
    };
  },
  computed: {
    selectedUser() {
      if (this.selectUser === 0) {
        return null;
      }
      const filteredUsers = this.user.filter((user) => user.id === this.selectUser);
      return filteredUsers[0];
    },
    notSelectedUsers() {
      return this.user.filter((user) => user.id !== this.selectUser);
    },
  },
  methods: {
    handleSelect(userId) {
      if (this.selectUser === userId) {
        this.selectUser = 0;
      } else {
        this.selectUser = userId;
      }
    },
  },
};
</script>

<style lang="scss">
.user {
    margin-bottom: 20px;
    text-align: center;
}
.user__selected {
    display: flex;
    font-size: 20px;
    margin-bottom: 10px;
}
.user__id {
    padding-left: 10px;
}
.user__not-selected {
    list-style-type: none;
    margin: 0;
    padding: 0;
}
.user__not-selected-item {
    display: flex;
    text-decoration: line-through;
}
</style>
