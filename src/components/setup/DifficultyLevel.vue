<template>
  <h3 class="mt-4 mb-3">{{t('setup.difficultyLevel.title')}}</h3>

  <div class="row">
    <div class="col-2 col-md-1 text-end">
      <label for="difficultyLevel" class="form-label">{{t('setup.difficultyLevel.easy')}}</label>
    </div>
    <div class="col-8 col-md-4">
      <input type="range" class="form-range" min="1" max="6" id="difficultyLevel"
          :value="$store.state.setup.difficultyLevel" @input="updateDifficultyLevel($event)">
    </div>
    <div class="col-2 col-md-1">
      <label for="difficultyLevel" class="form-label">{{t('setup.difficultyLevel.hard')}}</label>
    </div>
  </div>
  <div class="row">
    <div class="offset-2 offset-md-1 col-8 col-md-4 text-muted small">
      {{t(`difficultyLevel.${$store.state.setup.difficultyLevel}`)}}
    </div>
  </div>  

</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { useI18n } from 'vue-i18n'
import { useStore } from '@/store'

export default defineComponent({
  name: 'DifficultyLevel',
  setup() {
    const { t } = useI18n()
    useStore()
    return { t }
  },
  methods: {
    updateDifficultyLevel(event: Event) {
      const level = parseInt((event.target as HTMLInputElement).value)
      this.$store.commit('setupDifficultyLevel', level)
    }
  }
})
</script>
