<template>
    <router-link
        v-if="field.value && field.showAsLink"
        :to="{
            name: 'detail',
            params: {
                resourceName: resourceName,
                resourceId: field.value
            }
        }"
        class="no-underline dim text-primary font-bold"
    >
        {{ parentFieldLabel }}
    </router-link>

    <span v-else-if="field.value && !field.showAsLink" class="whitespace-no-wrap text-left">{{ parentFieldLabel }}</span>

    <span v-else class="whitespace-no-wrap text-left">&mdash;</span>
</template>

<script>
    export default {
        props: ['resourceName', 'field'],
        computed: {
            parentFieldLabel() {
                let label = ''

                this.field.options.forEach((option) => {
                    if (option.id === this.field.value) {
                        label = option.text
                    }
                })

                return label
            },
        }
    }
</script>
