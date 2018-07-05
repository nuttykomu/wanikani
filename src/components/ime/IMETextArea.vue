<template>
    <div>
        <h3>Input Mode:</h3>

        <input
            type="radio"
            value="ひらがな"
            v-model="mode"
            @change="text = ''">
        ひらがな<br>

        <input
            type="radio"
            value="カタカナ"
            v-model="mode"
            @change="text = ''">
        カタカナ

        <br><br>
        <textarea
            rows="1"
            maxlength="16"
            ref="textarea"
            v-model="text"
            @input="update"
            @keydown.enter.prevent
            @keydown.space.prevent>
        </textarea>
    </div>
</template>

<script>
import HiraganaMap from './HiraganaMap';
import KatakanaMap from './KatakanaMap';

const CHARACTER_MAP = {
    'ひらがな': HiraganaMap,
    'カタカナ': KatakanaMap
};

export default {
    data () {
        return {
            text: '',
            mode: 'ひらがな'
        }
    },
    methods: {
        update () {
            const filters = {
                'ひらがな': /[^a-zA-Z\u3040-\u309F\-\\s+]/g,
                'カタカナ': /[^a-zA-Z\u30A0-\u30FF\-\\s+]/g
            };

            this.text = this.text.replace(filters[this.mode], '');
            this.text = this.text.toUpperCase();

            CHARACTER_MAP[this.mode].forEach(mapping => {
                this.text = this.text.replace(mapping.romaji, mapping.kana);
            });
        }
    }
};
</script>

<style scoped>
div {
    font-size: 20px;
}

textarea {
    font-family: PixelMplus;
    overflow: hidden;
    font-size: 24px;
    resize: none;
    height: 24px;
    width: 20%;
    padding: 20px;
}
</style>
