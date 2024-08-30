<script>
  import ToDoList from './components/ToDoList.vue'
  import InputSection from './components/InputSection.vue'
  export default {
    components: { ToDoList, InputSection },
    data() {
      return {
        isVisibleElement: false,
        isChecked: false,
        toDoList: [],
      }
    },
    methods: {
      toggleIsVisibleElement() {
        this.isVisibleElement = !this.isVisibleElement
      },
      addNewItem(item, array) {
        item && array.unshift(item.trim())
      },
      removeItem(index, array) {
        array.splice(index, 1)
      },
    }
  }
</script>
<template>
  <div className="content__wrapper">
    <ToDoList 
      :toDoList="toDoList" 
      :removeItem="removeItem"
    />
    <InputSection 
      :isVisibleElement="isVisibleElement"
      :addNewItem="addNewItem"
      :toggleIsVisibleElement="toggleIsVisibleElement"
      :toDoList="toDoList"
    />
    <button
      className="button button_big"
      @click="toggleIsVisibleElement()"
      v-if="!isVisibleElement">
      <img src="./components/img/cross.svg" alt="cross">
    </button>
  </div>
</template>

<style lang="scss">
  @use './assets/main.scss' as *;
  @use './components/_mixins.scss' as *;

  .content__wrapper {
    width: 700px;
    min-height: 100vh;
    background-color: #252525;
    border-radius: 20px;
    position: relative;
    padding: 2rem;

    .button {
      @include button;

      img {
        width: 50px;
      }
    }
    .button_big {
      @include button_big
    }
  }
</style>
