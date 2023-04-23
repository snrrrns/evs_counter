<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold">努力値カウンター for SV</h1>
    <p class="mb-8"><small>ポケットモンスター スカーレット/バイオレット向け努力値カウンター</small></p>

    <div class="flex flex-row gap-4">
      <div class="w-full whitespace-nowrap">
        <div class="flex flex-row gap-6 items-center mb-5">
          <h3 class="w-1/12">HP</h3>
          <InputEffortValue v-model="hp.target" label="目標" />
          <InputEffortValue v-model="hp.current" label="現在" />
          <p>{{ `目標まで：${remainingValue(hp)}` }}</p>
        </div>
        <div class="flex flex-row gap-6 items-center mb-5">
          <h3 class="w-1/12">こうげき</h3>
          <InputEffortValue v-model="attack.target" label="目標" />
          <InputEffortValue v-model="attack.current" label="現在" />
          <p>{{ `目標まで：${remainingValue(attack)}` }}</p>
        </div>
        <div class="flex flex-row gap-6 items-center mb-5">
          <h3 class="w-1/12">ぼうぎょ</h3>
          <InputEffortValue v-model="defense.target" label="目標" />
          <InputEffortValue v-model="defense.current" label="現在" />
          <p>{{ `目標まで：${remainingValue(defense)}` }}</p>
        </div>
        <div class="flex flex-row gap-6 items-center mb-5">
          <h3 class="w-1/12">とくこう</h3>
          <InputEffortValue v-model="specialAttack.target" label="目標" />
          <InputEffortValue v-model="specialAttack.current" label="現在" />
          <p>{{ `目標まで：${remainingValue(specialAttack)}` }}</p>
        </div>
        <div class="flex flex-row gap-6 items-center mb-5">
          <h3 class="w-1/12">とくぼう</h3>
          <InputEffortValue v-model="specialAttack.target" label="目標" />
          <InputEffortValue v-model="specialAttack.current" label="現在" />
          <p>{{ `目標まで：${remainingValue(specialDefense)}` }}</p>
        </div>
        <div class="flex flex-row gap-6 items-center mb-5">
          <h3 class="w-1/12">すばやさ</h3>
          <InputEffortValue v-model="speed.target" label="目標" />
          <InputEffortValue v-model="speed.current" label="現在" />
          <p>{{ `目標まで：${remainingValue(speed)}` }}</p>
        </div>
      </div>
    </div>

    <p class="mt-8">{{ `現在の努力値合計：${remainingTotal}/${total}` }}</p>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import InputEffortValue from '~/components/form/InputEffortValue.vue';

type Params = {
  target: string,
  current: string,
}

type EffortValues = {
  hp: Params,
  attack: Params,
  defense: Params,
  specialAttack: Params,
  specialDefense: Params,
  speed: Params,
  total: number,
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
      hp: {
        target: '0',
        current: '0',
      },
      attack: {
        target: '0',
        current: '0',
      },
      defense: {
        target: '0',
        current: '0',
      },
      specialAttack: {
        target: '0',
        current: '0',
      },
      specialDefense: {
        target: '0',
        current: '0',
      },
      speed: {
        target: '0',
        current: '0',
      },
      total: 510,
    };
  },
  computed: {
    remainingTotal() {
      const sumCurrentValue: number = Object.values(this)
        .filter(value => typeof value === 'object')
        .reduce((sum, value) => sum + parseInt(value.current), 0);
      return sumCurrentValue;
    }
  },
  methods: {
    remainingValue(value: Params) {
      return parseInt(value.target, 10) - parseInt(value.current, 10);
    }
  }
});
</script>
