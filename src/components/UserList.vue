<template>
    <ul class="user__list">
        <li class="user__item" v-for="user in users" :key="user.id">
            <button class="user__btn" :class="selectUser === user.id ? 'user__btn--active' : ''"
                @click="handleSelect(user.id)">
                {{user.name}}
            </button>
        </li>

    </ul>
</template>
<script>
export default {
  props: {
    users: {
      type: Array,
      default: () => [],
    },
    selectUser: {
      type: Number,
      default: () => 0,
    },
  },
  methods: {
    handleSelect(userId) {
      this.$emit('handleSelect', userId);
    },
  },
};
</script>

<style lang="scss">
.user__list {
    display: flex;
    flex-direction: column;
    list-style-type: none;
    margin: 0;
    padding: 0;
}
.user__item {
    margin-bottom: 10px;
}
.user__btn {
    padding: 6px 12px;
    border-radius: 5px;
    border: none;
    background-color: #dae0e5;
    color: #000;
    transition: background-color .3s;
    cursor: pointer;
}
.user__btn--active {
    background-color: #007bff;
    transition: background-color .3s;
    color: white;
}
</style>
