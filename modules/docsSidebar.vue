<!-- eslint-disable -->
<template>
    <aside>
        <ul>
        <li
            v-for="link in articles"
            :key="link.id"
            :class="{ 'toc2': link.depth === 2, 'toc3': link.depth === 3 }"
        >
            <NuxtLink :to="`${link.path}`">{{ link.title }}</NuxtLink>
        </li>
        </ul>
    </aside>
</template>
<script lang="js">
export default {
    components: {

    },

    props: {
        articles: {
            type: Array,
            default: null
        }
    },

    data: () => ({
    }),

    computed: {
    },

    created() {
    },

    methods: {
    },

};
</script>
<!-- eslint-enable -->