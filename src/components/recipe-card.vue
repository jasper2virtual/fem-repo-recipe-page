<template>
    <div class="card">
        <img class="top-image" src="/src/assets/image-omelette.jpeg" alt="">
        <div class="text-content">
            <section class="title">
                <header class="header">
                    Simple Omelette Recipe
                </header>
                <p class="content">
                    An easy and quick dish, perfect for any meal. This classic omelette combines beaten eggs cooked
                    to perfection, optionally filled with your choice of cheese, vegetables, or meats.
                </p>
            </section>

            <section class="preparation">
                <header class="header">Preparation time</header>
                <ul class="list">
                    <li v-for="[label, text] in arrayUnflatten(
                        [
                            'Total', 'Approximately 10 minutes',
                            'Preparation', '5 minutes',
                            'Cooking', '5 minutes'
                        ], 2)"><span class="label">{{ label }}</span>: {{ text }}</li>
                </ul>
            </section>

            <section class="ingredients">
                <header class="header">Ingredients</header>
                <ul class="list">
                    <li v-for="ingredient in [
                        '2-3 large eggs',
                        'Salt, to taste',
                        'Pepper, to taste',
                        '1 tablespoon of butter or oil',
                        'Optional fillings: cheese, diced vegetables, cooked meats, herbs'
                    ]">{{ ingredient }}</li>
                </ul>
            </section>
            <hr>
            <section class="instructions">
                <header class="header">Instructions</header>
                <ul class="list">
                    <li v-for="[step, detail] in arrayUnflatten([
                        'Beat the eggs', 'In a bowl, beat the eggs with a pinch of salt and pepper until they are well mixed. You can add a tablespoon of water or milk for a fluffier texture.',
                        'Heat the pan', 'Place a non-stick frying pan over medium heat and add butter or oil.',
                        'Cook the omelette', 'Once the butter is melted and bubbling, pour in the eggs. Tilt the pan to ensure the eggs evenly coat the surface.',
                        'Add fillings (optional)', 'When the eggs begin to set at the edges but are still slightly runny in the middle, sprinkle your chosen fillings over one half of the omelette.',
                        'Fold and serve', 'As the omelette continues to cook, carefully lift one edge and fold it over the fillings. Let it cook for another minute, then slide it onto a plate.',
                        'Enjoy', 'Serve hot, with additional salt and pepper if needed.'
                    ], 2)">
                        <span class="step">{{ step }}</span>: {{ detail }}
                    </li>
                </ul>
            </section>
<hr>
            <section class="nutrition">
                <header class="header">Nutrition</header>
                <p>
                    The table below shows nutritional values per serving without the additional fillings.
                </p>
                <table class="nutrition-table">
                    <tbody>
                        <tr v-for="[nutrition, value] in
                            arrayUnflatten(
                                [
                                    'Calories', '277kcal',
                                    'Carbs', '0g',
                                    'Protein', '20g',
                                    'Fat', '22g'
                                ], 2
                            )">
                            <td class="nutrition">{{ nutrition }}</td>
                            <td class="value">{{ value }}</td>
                        </tr>

                    </tbody>
                </table>
            </section>


        </div>
    </div>
</template>
<script>
export default {
    methods: {
        arrayUnflatten(arr, chunkSize) {
            {
                return arr.reduce((result, value, index, array) => {
                    if (index % chunkSize === 0) {
                        result.push(array.slice(index, index + chunkSize));
                    }
                    return result;
                }, []);
            }
        }
    }
}
</script>
<style lang="scss" scoped>
.card {
    @apply flex flex-col;
    @apply bg-white;
    @apply max-w-[763px];
    @apply tablet:rounded-3xl;

    &>.top-image {
        @apply tablet:rounded-t-3xl;
    }

    &>.text-content {
        @apply flex flex-col gap-8;
        @apply px-8 py-10;


        &>.title {
            @apply flex flex-col gap-6;

            &>.header {
                @apply text-stone-900 text-preset-1;
            }

            &>.content {
                @apply text-stone-600 text-preset-4;
            }
        }

        &>.preparation {
            @apply flex flex-col gap-4 p-6 bg-rose-50 rounded-xl;

            &>.header {
                @apply text-rose-800 text-preset-3;
            }

            &>.list {
                @apply list-disc list-inside flex flex-col gap-2 pl-2 text-preset-4;

                &>li {
                    @apply marker:mr-4;

                    &>.label {
                        @apply text-preset-4-bold;
                    }
                }
            }
        }

        &>.ingredients {
            @apply flex flex-col gap-6;

            &>.header {
                @apply text-brown-800 text-preset-2;
            }

            &>.list {
                @apply list-disc list-inside flex flex-col gap-2 pl-2 text-preset-4;

                &>li {
                    @apply marker:mr-4;

                }

            }
        }

        &>.instructions {
            @apply flex flex-col gap-6;

            &>.header {
                @apply text-brown-800 text-preset-2;
            }

            &>.list {
                @apply list-decimal flex flex-col gap-2 pl-2 text-preset-4 ml-4;

                &>li {
                    @apply marker:text-preset-4-bold text-stone-600 marker:text-brown-800;

                    &>.step {
                        @apply text-preset-4-bold;
                    }
                }
            }
        }

        &>.nutrition {
            @apply flex flex-col gap-6;

            &>.header {
                @apply text-brown-800 text-preset-2;
            }

            &>p {
                @apply text-stone-600 text-preset-4;
            }

            &>.nutrition-table {
                &>tbody {
                    &>tr {
                        &>td {
                            @apply py-[6px];
                        }

                        &>.nutrition {
                            @apply text-stone-600 text-preset-4;
                        }

                        &>.value {
                            @apply text-brown-800 text-preset-4-bold;
                        }
                    }
                    &>tr:not(:last-child){
                        @apply border-b;
                    }
                }
            }
        }

    }
}
</style>