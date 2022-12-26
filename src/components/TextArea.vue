<script setup>
    import { ref, computed } from "vue";

    const props = defineProps({
        labelText: {
            type: String,
            required: true,
            default: ""
        },
        validationRegex: {
            type: String,
            required: false,
            default: ""
        },
        isRequired: {
            type: Boolean,
            required: true,
            default: true
        }
    })

    const textAreaState = ref("");
    const labelTextToShow = ref("");
    const textAreaValue = ref("");
    const rowsAmount = ref(1);

    const classObj = computed(() => ({
        ready: textAreaState.value === "ready",
        error: textAreaState.value === "error",
        sent: textAreaState.value === "sent"
    }))

    function validateTextArea() {
        if (!textAreaValue.value && props.isRequired) {
            textAreaState.value = "error";
            labelTextToShow.value = "* Это поле обязательно";
        } else if (props.validationRegex && !props.validationRegex.test(textAreaValue.value)) {
            textAreaState.value = "error";
            labelTextToShow.value = "Неправильно введенное значение";
        } else if (textAreaValue.value) {
            textAreaState.value = "ready";
            labelTextToShow.value = props.labelText;
        }
    }

    function calcAndChangeHeight({ target }) {
        const rowsToSet = Math.floor(target.scrollHeight / target.cols);
        rowsAmount.value = rowsToSet < 1 || !target.textLength ? 1 : rowsToSet;
    }
</script>

<template>
    <div class="textarea-wrapper" :class="classObj">
        <label for="input" v-if="labelTextToShow">
            {{ labelTextToShow }}
        </label>
        <textarea
            v-bind="$attrs"
            v-model="textAreaValue"
            type="text"
            name="input"
            :rows="rowsAmount"
            spellcheck="false"
            @input="calcAndChangeHeight"
            @blur="validateTextArea"
        ></textarea>
    </div>
</template>

<style scoped>
    .textarea-wrapper {
        display: flex;
        flex-direction: column;

        --active-label-color: #000;
        --active-textarea-bg-color: transparent;
        --active-textarea-stroke-color: #000;
    }
    .textarea-wrapper.ready {
        --active-label-color: #8CB1C7;
        --active-textarea-bg-color: #E0F2FD;
        --active-textarea-stroke-color: #8CB1C7;
    }
    .textarea-wrapper.error {
        --active-label-color: #FB8888;
        --active-textarea-bg-color: transparent;
        --active-textarea-stroke-color: #FC9797;
    }
    .textarea-wrapper.sent {
        --active-label-color: #A0BC97;
        --active-textarea-bg-color: #E3FDE0;
        --active-textarea-stroke-color: #A0BC97;
    }
    label {
        padding-left: 20px;
        font: 600 10px/12px var(--font-inter);
        color: var(--active-label-color);

        will-change: color;
        transition: all 0.2s ease-in-out;
    }
    textarea {
        background-color: var(--active-textarea-bg-color);
        border: var(--active-textarea-stroke-color) 1px solid;
        border-radius: 10px;
        padding: 6px 20px;
        font: var(--default-font);
        resize: none;
        will-change: outline;
        transition: all 0.2s ease-in-out;
    }
    textarea::placeholder {
        opacity: 0.8;
    }
    textarea:focus {
        outline: var(--active-textarea-stroke-color) 1px solid;
    }
</style>

