<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-4">努力値カウンター</h1>
    
    <div class="flex flex-col md:flex-row gap-4">
      <div class="w-full md:w-1/2">
        <div class="flex flex-row gap-4">
          <div class="w-1/3">
            <label class="block font-medium mb-2" for="hp">HP</label>
            <input
              v-model.number="effortValues.hp"
              type="number"
              min="0"
              max="252"
              id="hp"
              name="hp"
              class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4"
            />
          </div>
          <div class="w-1/3">
            <label class="block font-medium mb-2" for="attack">こうげき</label>
            <input
              v-model.number="effortValues.attack"
              type="number"
              min="0"
              max="252"
              id="attack"
              name="attack"
              class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4"
            />
          </div>
          <div class="w-1/3">
            <label class="block font-medium mb-2" for="defense">ぼうぎょ</label>
            <input
              v-model.number="effortValues.defense"
              type="number"
              min="0"
              max="252"
              id="defense"
              name="defense"
              class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4" />
          </div>
        </div>
        
        <div class="flex flex-row gap-4">
          <div class="w-1/3">
            <label class="block font-medium mb-2" for="special-attack">とくこう</label>
            <input
              v-model.number="effortValues.specialAttack"
              type="number"
              min="0"
              max="252"
              id="special-attack"
              name="special-attack"
              class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4"
            />
          </div>
          <div class="w-1/3">
            <label class="block font-medium mb-2" for="special-defense">とくぼう</label>
            <input
              v-model.number="effortValues.specialDefense"
              type="number"
              min="0"
              max="252"
              id="special-defense"
              name="special-defense"
              class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4"
            />
          </div>
            <div class="w-1/3">
            <label class="block font-medium mb-2" for="speed">すばやさ</label>
            <input
              v-model.number="effortValues.speed"
              type="number"
              min="0"
              max="252"
              id="speed"
              name="speed"
              class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4"
            />
          </div>
        </div>

      </div>
    </div>
    <div class="mt-4">
      <h2 class="text-lg font-semibold mb-2">努力値合計</h2>
      <p class="text-xl font-semibold">{{ totalEffortValues }}</p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      effortValues: {
        hp: 0,
        attack: 0,
        defense: 0,
        specialAttack: 0,
        specialDefense: 0,
        speed: 0,
      },
    };
  },
  computed: {
    totalEffortValues() {
      return Object.values(this.effortValues).reduce((acc, val) => acc + val, 0);
    },
  },
};
</script>