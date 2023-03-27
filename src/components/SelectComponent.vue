<template>
    <div class="flex justify-between px-4 font-bold my-2 items-center">
        <label>{{ label }}</label>
        <select class="w-3/4 rounded-md px-4 py-2 text-violet-700" :value="modelValue"
            @change="$emit('update:modelValue', $event.target.value)" v-bind="$attrs" :class="{ 'is-invalid': getError() }">
            <option value="" v-if="placeholder">{{ placeholder }}</option>
            <option v-for="option in options" :key="`option-${option.value}`" :value="option.text">
                {{ option.text }}
            </option>
        </select>
    </div>
    <div class="text-[14px] text-red-500 z-999 font-bold text-center" v-if="getError()">{{ getError() }}</div>
</template>
<script>
export default {
    inheritAttrs: false,
    props: {
        label: {
            type: String,
            required: true,
        },
        modelValue: {
            type: [String, Number],
            default: null,
        },
        options: {
            type: Array,
            required: true,
        },
        placeholder: {
            type: String,
            default: "",
        },
        error: {
            type: [Array, String],
            default: null,
        },
    },
    methods: {
        getError() {
            if (!this.modelValue && this.placeholder) {
                return Array.isArray(this.error) ? this.error.join(", ") : this.error;
            }
            return false;
        },
    },
};
</script>
  