<template>
    <div class="note-form__wrapper">
        <form 
            @submit.prevent="onSubmit"
            class="note-form"
        >
            <textarea
                required
                v-model="value"
                :placeholder="placeholder"
            />
            <TagsList
                :isActive="aticveTags"
                :items="tags"
                @onTagLick="handleTagLick"
            />
            <button 
                class="btn btnPrimary" 
                type="submit"
                :style="{'margin-top': '30px'}"
            >
                Add new note
            </button>
        </form>
    </div>
</template>
<script>
import TagsList from '@/components/UI/TagsList.vue';
export default {
    components:{
        TagsList, 
    },
    data() {
      return {
            aticveTags:[],
            value: '',
            placeholder: 'Type your todo',
            tags: ['home', 'work', 'travel']
        };
    },
    methods: {
        onSubmit() {
            this.$emit('onSubmit2', { title: this.value, tags: this.aticveTags });
            this.value = "";
        },
        handleTagLick(tag){
            let index = this.aticveTags.indexOf(tag);
            if (index !== -1) {
                this.aticveTags.splice(index, 1);
            } else {
                this.aticveTags.push(tag)
            }
            
        }
    },
}
</script>
<style scoped>

.note-form__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding:45px 0 0;
}
.note-form {
  display: flex;
  flex-direction: column;
  max-width: 600px;
  width: 100%;
  textarea {
    margin-bottom: 0px;
  }
}
</style>