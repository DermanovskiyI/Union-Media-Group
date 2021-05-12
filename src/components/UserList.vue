<template>
    <ul class="user__list">
        <li class="user__item">
            <button class="user__btn">Вася</button>
        </li>
        <li class="user__item">
            <button class="user__btn user__btn--active">Вася</button>
        </li>
        <li class="user__item">
            <button class="user__btn" type="button">Вася</button>
        </li>

    </ul>
</template>
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
