<template>
    <div class="tags-list">
      <div
        class="tag-item"
        v-for="item in items"
        :key="item"
        @click="$emit('onTagLick', item)"
        :class="{ isPreview: isPreview, 'isActive': isActive && isActive.indexOf(item) !== -1 }"
      >
        <span>{{ item }}</span>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      items:{
        type:Array,
        required:true,
      },
      isPreview:{
        type:Boolean,
        required:false,
      },
      isActive: {
        type: Array,
        required: false
      },
    },
    data(){
      return{

      }
    }
  }
  </script>
  
  <style lang="scss">
  .tags-list {
    padding: 10px 0;
    display: flex;
    justify-content: center;
  }
  .tag-item {
    padding: 8px 22px;
    margin-right: 10px;
    background-color: #fff;
    border-radius: 22px;
    user-select: none;
    cursor: pointer;
    transition: 0.3s ease;
    &.isActive {
      background-color: #444ce0;
      color: #fff;
    }
    &.isPreview {
      padding: 0;
      color: #444ce0;
      cursor: default;
      &:before {
        content: '#';
      }
      &:hover{
        background-color: #fff;
        color:#444ce0;
      }
    }
    &:last-child {
      margin-right: 0;
    }
    &:hover{
      background-color: #444ce0;
      color:#fff;
    }
  }
  </style>
  