<script>

export default {
    data() {
        return {
            recipes: [],
            recipeName: '',
            recipeDescription: '',
            id: 0,
            editValue: "",
            ok: false,
            updateRecipe: {
                recipeName: '',
                recipeDescription: '',
                recipeIngredients: [''],
            },
        }
    },
    methods: {
        saveRecipe(recipe) {

            this.recipe.push(this.updateRecipe)

            console.log(this.recipeName);
            console.log(recipe.recipeName);

        },
    }

};
</script>

<template>
    <h1>Edit Recipe</h1>
    <div>
        <form @submit.prevent="saveRecipe">
            <input id="name" type="text" v-model="editInput" /><br />
            <textarea id="description"></textarea>
            <ul>
                <li></li>
                <li></li>
            </ul>
            <input id="name" type="text" value="" /><br />
            <button>Add Ingredients</button><br />
            <button type="submit">Save</button>
        </form>
    </div>
</template>


<style scoped>
.read-the-docs {
    color: #888;
}
</style>
