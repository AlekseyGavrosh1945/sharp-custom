<template>
    <div class="SharpFilterCheck form-check mt-1 mx-2">
        <input
            :id="id"
            class="form-check-input"
            type="checkbox"
            :name="filterKey"
            :checked="value"
            :disabled="disabled"
            @change="handleChanged"
        >
        <label class="ui-font fs-8" :for="id">
            {{ label }}
        </label>
    </div>
</template>

<script>
    export default {
        props: {
            filterKey: String,
            label: String,
            value: Boolean,
            disabled: Boolean,
        },
        computed: {
            id() {
                return `filter-${this.filterKey}`
            },
        },
        methods: {
            handleChanged(e) {
                // Эмитим input для обновления UI и pending-change для отложенного применения
                this.$emit('input', e.target.checked);
                this.$emit('pending-change', e.target.checked);
            },
        },
    }
</script>
