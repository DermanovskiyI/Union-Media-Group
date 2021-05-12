<template>
    <div class="container">
        <div class="result">
            <div class="result__selected" v-if="selectedUser">
                <div class="result__name">{{selectedUser.name}}</div>
                <div class="result__id">{{selectedUser.id}}</div>
            </div>
            <ul class="result__not-selected">
                <li class="result__not-selected-item" v-for="user in notSelectedUsers"
                    :key="user.id">
                    <div class="result__name">{{user.name}}</div>
                    <div class="result__id">{{user.id}}</div>
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
.result {
    margin-bottom: 20px;
    text-align: center;
}
.result__selected {
    display: flex;
    font-size: 20px;
    margin-bottom: 10px;
}
.result__id {
    padding-left: 10px;
}
.result__not-selected {
    list-style-type: none;
    margin: 0;
    padding: 0;
}
.result__not-selected-item {
    display: flex;
    text-decoration: line-through;
}
</style>
