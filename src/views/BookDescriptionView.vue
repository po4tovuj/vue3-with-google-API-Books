<template>
    <div v-if="book && !loading && !error" class="book-card-wapper">
        <book-card :book="book"></book-card>
    </div>

    <loading-spiner v-if="loading"></loading-spiner>
    
    <div v-if="(!loading && !book) || error" class="not-found-wrapper">
        <h2 class="not-found">No Books Found!</h2>
    </div>
</template>

<script lang="ts">
import { defineComponent, toRefs } from 'vue';
import BookCard from '~/components/BookCard.vue';
import LoadingSpiner from '~/components/LoadingSpiner.vue';
import { useBookDetails } from '~/composables/useGetBooks';

export default defineComponent({
    name: 'BookDescriptionView',
    components: { BookCard, LoadingSpiner },
    props: ['id', 'description'],
    setup(props) {
        const { id } = toRefs(props);
        const { book, loading, error } = useBookDetails(`${id.value}`);

        return {
            book,
            loading,
            error,
        };
    },
});
</script>
<style lang="scss">
.not-found-wrapper {
    color: red;
    .not-found {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
}
</style>
