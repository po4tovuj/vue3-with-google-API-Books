<template>
    <div class="filters-wrapper">
        <ul class="filters-list">
            <li class="filter-search">
                <label class="filter-search__label" for="authorSearch">
                    Search by author
                    <div class="filter-search__icon">
                        <input
                            id="authorSearch"
                            type="search"
                            placeholder="Search Author"
                            class="filter-search__input"
                            @keypress.enter="searchBook"
                            v-model="authorSearch"
                        />
                    </div>
                </label>
            </li>
            <li class="filter-search">
                <label class="filter-search__label" for="search">
                    Global Search

                    <div class="filter-search__icon">
                        <input
                            id="search"
                            type="search"
                            placeholder="Search"
                            class="filter-search__input"
                            @keypress.enter="searchBook"
                            v-model="searchQuery"
                        />
                    </div>
                </label>
            </li>
        </ul>
    </div>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
    emits: ['handleSearch'],
    setup(_, { emit }) {
        const searchQuery = ref<string>('');
        const authorSearch = ref<string>('');

        const searchBook = () => {
            emit('handleSearch', {
                searchQuery: searchQuery.value,
                authorSearch: authorSearch.value,
            });
        };

        return { searchQuery, authorSearch, searchBook };
    },
});
</script>

<style scoped lang="scss">
.filters-wrapper {
    .filters-list {
        padding: 0;
        margin: 0;
        list-style-type: none;
        display: flex;
        justify-content: flex-end;
        padding: 20px 40px;
        background-color: #6f10eb;

        .filter-search {
            &__label {
                color: #fff;
                font-size: 16px;
                display: block;
                margin-bottom: 0.25rem;
                text-align: left;
                margin-left: 20px;
            }
            &__input {
                display: block;
                width: 100%;
                height: calc(2rem + 2px);
                padding: 0.375rem 0.75rem;
                font-family: inherit;
                font-size: 1rem;
                font-weight: inherit;
                line-height: 1.5;
                color: #212529;
                background-color: #fff;
                background-clip: padding-box;
                border: 1px solid #bdbdbd;
                border-radius: 0.25rem;
                transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
                -webkit-appearance: none;
                -moz-appearance: none;
                appearance: none;
                &::placeholder {
                    color: #212529;
                    opacity: 0.4;
                }
                &:focus {
                    color: #212529;
                    background-color: #fff;
                    border-color: #bdbdbd;
                    outline: 0;
                    box-shadow: 0 0 0 0.2rem rgba(158, 158, 158, 0.25);
                }
            }
            &__icon {
                position: relative;
                &::before {
                    content: '';
                    position: absolute;
                    top: 0;
                    bottom: 0;
                    left: 0;
                    width: 2.5rem;
                    background-color: #f5f5f5;
                    border: 1px solid #bdbdbd;
                    border-top-left-radius: 0.25rem;
                    border-bottom-left-radius: 0.25rem;
                }
                &::after {
                    content: '';
                    color: #212529;
                    position: absolute;
                    display: flex;
                    align-items: center;
                    top: 0;
                    bottom: 0;
                    width: 2.5rem;
                    top: 50%;
                    transform: translateY(-50%);
                    justify-content: center;
                    width: 2.5rem;
                    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='%23212529' viewBox='0 0 16 16'%3E%3Cpath d='M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z'%3E%3C/path%3E%3C/svg%3E");
                    background-repeat: no-repeat;
                    background-position: center;
                }
                .filter-search__input {
                    padding-left: 3rem;
                }
            }
        }
    }
}
</style>
