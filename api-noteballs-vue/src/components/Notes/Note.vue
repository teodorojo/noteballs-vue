<template>
    <div 
     class="card mb-4">
      <!-- <header class="card-header">
        <p class="card-header-title">Título 1</p>
        <button class="card-header-icon" aria-label="more options">S
          <span class="icon">
            <i class="fas fa-angle-down" aria-hidden="true"></i>
          </span>
        </button>
      </header> -->
      <div class="card-content">
        <div class="content">
          {{ note.content }}
          <div class="has-text-right has-text-grey-light mt-2">
            <small> {{ characterLength }}</small>
          </div>
        </div>
      </div>
      <footer class="card-footer">
        <RouterLink
         href="#" 
        :to="`/editNote/${ note.id }`"
         class="card-footer-item">
             Editar
        </RouterLink>
        <a  
         @click.prevent="storeNotes.deleteNote(note.id)"
         href="#" 
         class="card-footer-item"
        >
         Deletar
        </a>
      </footer>
    </div>
</template>

<script setup>
import { computed, onMounted } from 'vue';
import { useStoreNotes } from '../../stores/storeNotes';

const storeNotes = useStoreNotes();

const props = defineProps({
    note: {
        type: Object,
        required: true,
    }
})

onMounted(() => {
  console.log(props.note)
})

const characterLength = computed(() => {
    let length = props.note.content.length;
    let description = length > 1 ? 'caracteres' : 'caracter';
    return `${length} ${description}`
})
</script>