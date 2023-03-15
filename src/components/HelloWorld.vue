<script>
import EditRecipe from './EditRecipe.vue'

export default {
  data() {
    return {
      recipes: [],
      recipeName: '',
      recipeDescription: '',
      id: 0,
      inputValue: "",
      ok: false,
      updateRecipe: {
        recipeName: '',
        recipeDescription: '',
        recipeIngredients: [''],
      },
    }
  },
  components: {
    EditRecipe
  },
  methods: {
    addRecipe() {
      this.recipes.push({
        recipeName: this.inputValue,
        recipeDescription: '',
        id: this.id++,
        recipeIngredients: this.recipeIngredients
      });
      this.inputValue = "";
    },
    deleteRecipe(index) {
      this.recipes.splice(index, 1)
    },
    editRecipe(recipe) {
      this.ok = true;
      let name = document.getElementById("name");
      let description = document.getElementById("description");
      let edit = document.getElementById("edit");
      this.updateRecipe = recipe;
      name.value = recipe.recipeName;
      description.value = recipe.recipeDescription;
      edit.style.display = "block";

    },
  }
};

</script>

<template>
  <h1>Add Recipe</h1>
  <form @submit.prevent="addRecipe">

    <input type="text" v-model="inputValue">
    <button type="submit">Add</button>
  </form>

  <ul>
    <li v-for="(recipe, index) in recipes" :key="index">
      {{ recipe.recipeName }}
      <button @click="editRecipe(recipe)">Edit</button>
      <button @click="deleteRecipe(index)">Supprimer</button>
    </li>
    <div id="edit" style="display: none;">
      <EditRecipe />
    </div>
  </ul>
</template>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
