<template>
  <figure class="md:p-9 md:rounded-t-3xl bg-white">
    <img :src="recipe.image" alt="Omelette image" class="md:rounded-xl" />
  </figure>
  <article class="flex flex-col p-9 md:pt-0 md:rounded-b-3xl gap-9 bg-white">
    <header class="flex flex-col gap-5">
      <h1 class="m-0 text-4xl text-stone-900">{{ recipe.title }}</h1>
      <p>
        {{ recipe.description }}
      </p>
    </header>
    <section class="p-5 rounded-xl bg-rose-50">
      <h3 class="mb-2 text-rose-800">
        {{ recipe.subtitle.prepTime }}
      </h3>
      <ul
        class="pl-5 list-outside list-disc text-stone-600 space-y-3 marker:text-rose-800"
      >
        <li
          v-for="(item, index) in recipe.preparation"
          :key="index"
          class="pl-3 md:pl-5"
        >
          <b>{{ item.title }}</b
          >{{ item.description }}
        </li>
      </ul>
    </section>
    <section>
      <h2>Ingredients</h2>
      <ul class="pl-5 list-outside space-y-3 list-disc marker:text-brown-800">
        <li
          v-for="(ingredients, index) in recipe.ingredients"
          :key="index"
          class="pl-3 md:pl-5"
        >
          {{ ingredients }}
        </li>
      </ul>
    </section>
    <hr />
    <section>
      <h2>Instructions</h2>
      <ol
        class="pl-5 md:pl-6 list-outside space-y-3 list-decimal marker:text-brown-800 marker:font-bold"
      >
        <li
          v-for="(step, index) in recipe.instructions"
          :key="index"
          class="pl-3 md:pl-5"
        >
          <b>{{ step.title }}</b>
          {{ step.description }}
        </li>
      </ol>
    </section>
    <hr />
    <section>
      <h2>Nutrition</h2>
      <p>
        The table below shows nutritional values per serving without the
        additional fillings.
      </p>
      <table class="w-full mt-5">
        <tbody>
          <tr
            :class="{
              'border-b border-stone-150':
                index !== Object.entries(recipe.nutrition).length - 1,
            }"
            v-for="([key, value], index) in Object.entries(recipe.nutrition)"
            :key="index"
          >
            <td class="w-1/2 h-12 pl-8 capitalize">{{ key }}</td>
            <td class="pl-5 font-bold text-brown-800">{{ value }}</td>
          </tr>
        </tbody>
      </table>
    </section>
  </article>
</template>

<script setup>
import { ref } from "vue";

const recipe = ref({
  title: "Simple Omelette Recipe",
  description:
    "An easy and quick dish, perfect for any meal. This classic omelette combines beaten eggs cooked to perfection, optionally filled with your choice of cheese, vegetables, or meats.",
  image: "./image-omelette.jpeg",
  subtitle: {
    prepTime: "Preparation time",
    ingredients: "Ingredients",
    instructions: "Instructions",
  },
  preparation: [
    { title: "Total: ", description: "Approximately 10 minutes" },
    { title: "Preparation: ", description: "5 minutes" },
    { title: "Cooking: ", description: "5 minutes" },
  ],
  ingredients: [
    "2-3 large eggs",
    "Salt, to taste",
    "Pepper, to taste",
    "1 tablespoon of butter or oil",
    "Optional fillings: cheese, diced vegetables, cooked meats, herbs",
  ],
  instructions: [
    {
      title: "Beat the eggs:",
      description:
        "In a bowl, beat the eggs with a pinch of salt and pepper until they are well mixed. You can add a tablespoon of water or milk for a fluffier texture.",
    },
    {
      title: "Heat the pan:",
      description:
        "Place a non-stick frying pan over medium heat and add butter or oil.",
    },
    {
      title: "Cook the omelette:",
      description:
        "Once the butter is melted and bubbling, pour in the eggs. Tilt the pan to ensure the eggs evenly coat the surface.",
    },
    {
      title: "Add fillings (optional):",
      description:
        "When the eggs begin to set at the edges but are still slightly runny in the middle, sprinkle your chosen fillings over one half of the omelette.",
    },
    {
      title: "Fold and serve:",
      description:
        "As the omelette continues to cook, carefully lift one edge and fold it over the fillings. Let it cook for another minute, then slide it onto a plate.",
    },
    {
      title: "Enjoy:",
      description: "Serve hot, with additional salt and pepper if needed.",
    },
  ],
  nutrition: {
    calories: "277kcal",
    carbs: "0g",
    protein: "20g",
    fat: "22g",
  },
});
</script>

<style scoped>
article,
figure {
  min-width: 320px;
  max-width: 767px;
}
h2 {
  margin-bottom: 1.5rem;
  color: hsl(14, 45%, 36%);
}

h3 {
  font-family: var(--main-font);
  font-weight: 600;
}
h1,
h2 {
  font-family: var(--heading-font);
}
</style>
