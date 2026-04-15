<template>
    <div class="flex">
        <UISidebar class="hidden lg:flex duration-300 transition-all" />
        <section
            class="p-4 lg:p-6 duration-300 transition-all w-full rounded-tl-xl m-2 lg:m-0 lg:mt-2 border-l border-t border-border flex flex-col gap-6.5"
        >
            <slot />
        </section>
    </div>
</template>
