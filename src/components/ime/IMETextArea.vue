<template>
    <div>
        <textarea
            ref="textarea"
            v-model="text"
            @input="update">
        </textarea>
    </div>
</template>

<script>
import HiraganaMap from './HiraganaMap';

const CHARACTER_MAP = {
    'ひらがな': HiraganaMap,
    'カタカナ': []
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
                'ひらがな': /[^a-zA-Z\u3040-\u309F\n]/g,
                'カタカナ': /[^a-zA-Z\u30A0-\u30FF\n]/g
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
textarea {
    font-size: 24px;
    resize: none;
    height: 240px;
    width: 100%;
}
</style>
