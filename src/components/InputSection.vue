<script>
  export default {
    props: {
      isVisibleElement: {
        type: Boolean,
        required: true
      },
      addNewItem: {
        type: Function,
        required: true
      },     
      toggleIsVisibleElement: {
        type: Function,
        required: true
      },
      toDoList: {
        type: Array,
        required: true
      }
    },
    newItem: '',
    methods: {
      clearInput(newItem) {
        this.newItem = '';
      }
    }
  }
</script>
<template>
  <div className="input__wrapper" v-if="isVisibleElement" >
    <input type="text" v-model="newItem">
      <div class="buttons__wrapper">
        <button 
          className="button" 
          @click="addNewItem(newItem, toDoList); clearInput(); toggleIsVisibleElement()">
          <img src="./img/check-circle.svg" alt="check">
        </button>
        <button 
          className="button" 
          @click="toggleIsVisibleElement(); clearInput()">
          <img src="./img/ban.svg" alt="delete">
        </button>
      </div>
    </div>
</template>
<style lang="scss">
  @use '../assets/main.scss' as *;
  @use '../components/_mixins.scss' as *;

  .input__wrapper {
    height: 8rem;
    border-radius: 20px;
    position: absolute;
    bottom: 30px;
    left: 30px;
    right: 30px;
    display: grid;
    grid-template-columns: 1fr min-content;

    input {
      padding: 0 1rem;
      border: 0;
      border-radius: 10px;
      font-size: 1.5rem;
    }

    .buttons__wrapper {
      width: 100px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;

      .button {
        @include button
      }
    }
  }
</style>