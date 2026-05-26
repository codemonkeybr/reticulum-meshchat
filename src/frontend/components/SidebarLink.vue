<template>
    <RouterLink :to="to" v-slot="{ href, route, navigate, isActive }" custom>
        <a
            :href="href"
            @click="handleNavigate($event, navigate)"
            type="button"
            :class="[
                isActive
                    ? 'bg-blue-100 text-blue-800 group:text-blue-800 dark:bg-zinc-800 dark:text-blue-300'
                    : 'hover:bg-gray-100 dark:hover:bg-zinc-700',
                collapsed ? 'justify-center rounded-md mx-2 p-2' : 'rounded-r-full p-2 mr-2'
            ]"
            class="w-full text-gray-800 dark:text-zinc-200 group flex gap-x-3 text-sm leading-6 font-semibold focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-blue-600 dark:focus-visible:outline-zinc-500"
        >
            <span class="my-auto shrink-0">
                <slot name="icon"></slot>
            </span>
            <span v-show="!collapsed" class="my-auto flex w-full overflow-hidden whitespace-nowrap">
                <slot name="text"></slot>
            </span>
        </a>
    </RouterLink>
</template>


<script>
export default {
    name: 'SidebarLink',
    props: {
        to: Object,
        collapsed: {
            type: Boolean,
            default: false,
        },
    },
    methods: {
        handleNavigate(event, navigate) {
            this.$emit('click');
            navigate(event);
        },
    },
};
</script>
