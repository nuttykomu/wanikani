<template>
    <div id="app">
        <h1>IME Text Area</h1>
        <p>Type in the text box below. The text will automatically be replaced with hiragana characters.</p>
        <ime-textarea></ime-textarea>
    </div>
</template>

<script>
import IMETextArea from './components/ime/IMETextArea';

export default {
    name: 'app',
    components: {
        'ime-textarea': IMETextArea
    }
};
</script>

<style lang="scss">
div {
    margin: 20px;
}

h1, p {
    margin-left: 20px;
}
</style>
