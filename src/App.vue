<template>
    <div id="app">
        <h1>IME Text Area</h1>
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
@font-face {
    font-family: PixelMplus;
    src: url("./assets/PixelMplus12-Regular.ttf") format('truetype');
}

html {
    font-family: PixelMplus;
}

div {
    margin: 20px;
}

h1, p {
    margin-left: 20px;
}
</style>
