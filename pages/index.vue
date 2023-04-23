<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-4">努力値カウンター</h1>
    
    <div class="flex flex-col md:flex-row gap-4">
      <div class="w-full md:w-1/2">
        <InputEffortValue v-model="effortValues.hp" label="HP" />
        <InputEffortValue v-model="effortValues.attack" label="こうげき" />
        <InputEffortValue v-model="effortValues.defense" label="ぼうぎょ" /> 
        <InputEffortValue v-model="effortValues.specialAttack" label="とくこう" />
        <InputEffortValue v-model="effortValues.specialDefense" label="とくぼう" />
        <InputEffortValue v-model="effortValues.speed" label="すばやさ" /> 
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import InputEffortValue from '~/components/form/InputEffortValue.vue';

type Stats = {
  hp: string,
  attack: string,
  defense: string,
  specialAttack: string,
  specialDefense: string,
  speed: string,
}

type EffortValues = {
  effortValues: Stats,
}

export default defineComponent ({
  components: {
    InputEffortValue,
  },
  data(): EffortValues {
    return {
      /**
       * inputタグのvalueを制御するにはnumber型よりも
       * string型で受け渡す方が扱いやすい
       */
      effortValues: {
        hp: '0',
        attack: '0',
        defense: '0',
        specialAttack: '0',
        specialDefense: '0',
        speed: '0',
      },
    };
  },
});
</script>
