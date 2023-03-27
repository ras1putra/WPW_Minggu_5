<template>
    <div class="flex justify-between px-4 font-bold items-center my-2">
        <label class="my-auto">{{ label }}</label>
        <div class="w-3/4">
            <input class="w-full rounded-md p-2" v-bind="$attrs" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" :class="{ 'is-invalid': getError() }" />
            <div class="text-[14px] text-red-500 absolute z-999" v-if="getError()">{{ getError() }}</div>
        </div>
    </div>
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
        error: {
            type: [Array, String],
            default: null,
        },
    },
    created() {
        console.log(this.$attrs);
    },
    methods: {
        getError() {
            if (this.modelValue === "") {
                return Array.isArray(this.error) ? this.error.join(", ") : this.error;
            }
            return false;
        },
    },
};
</script>
  