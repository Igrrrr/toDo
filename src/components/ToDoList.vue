<script>
  export default {
    props: {
      toDoList: {
        type: Array,
        required: true
      },
      removeItem: {
        type: Function,
        required: true
      }
    }
  }
</script>
<template>
  <div className="toDo">
      <ul >
        <li v-for="(item, index) in toDoList" :key="index">
          <input type="checkbox">
          <p>{{ item }}</p>
          <button 
            className="button button_small" 
            @click="removeItem(index, toDoList)">
          <img src="./img/trash3.svg" alt="clear">
        </button>
        </li>
      </ul>
  </div>
</template>
<style lang="scss">
  @use '../assets/main.scss' as *;
  @use '../components/_mixins.scss' as *;

  .toDo {
    max-height: 100%;

    ul {
      width: 100%;
    }

      li {
        padding: 1rem;
        width: 100%;
        display: grid;
        grid-template-columns: 1rem 500px min-content;
        grid-template-rows: min-content;
        overflow-wrap: break-word;
        gap: 1rem;
        height: auto;
        border: 2px solid $font-dark-color;
        border-radius: 4px;
        margin-bottom: 1rem;
        font-size: 1.5rem;
      }

      p {
        color: white;
        list-style-type: 0;
        border-radius: 3px;
        padding: 0 1rem;
      }

      .button {
        @include button
      }

      .button_small {
        @include button_small;
      }
  }
</style>