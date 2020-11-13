<template>
  <div class="layout">
    <div class="col">
      <Panel heading="Редактируемый текст">
        <p class="text" 
          :style ="{
            color: styles.color,
            fontSize: styles.fontSize,
            backgroundColor: styles.backgroundColor
          }"
        >
          {{ text }}
        </p>
      </Panel>
      <div class="json">
        <Panel heading="Экспорт стилей">
          <pre>{{ json }}</pre>
          <Button @click="copyJSON">Скопировать</Button>
        </Panel>
      </div>
    </div>
    <div class="col">
      <Panel heading="Изменить стили">
        <Toolbar
          @change-bg="changeBackground"
          @change-color="changeColor"
          @change-font="changeFont"
        />
      </Panel>
    </div>
  </div>
</template>

<script>
import Toolbar from "./Toolbar";
import Panel from "./Panel";
import { copyToClipboard } from "../lib/copy-to-clipboard";
/**
 * Text editor component with a toolbar to change font and background
 * Also there is "export as JSON representation" feature
 */
export default {
  data() {
    return {
      styles: {
        fontSize: "20px",
        color: "#000000",
        backgroundColor: "#ffffff"
      },
      text: 'Загрузка...',
    };
  },
  computed: {
    json() {
      return JSON.stringify(this.styles);
    }
  },
  async created() {
    const response = await fetch('https://fish-text.ru/get');
    const json = await response.json();
    const { text } = json;
    this.text = text;
  },
  components: {
    Toolbar,
    Panel
  },
  methods: {
    changeTextElementStyle(styleName, newValue) {
      const { styles } = this;
      this.$set(styles, styleName, newValue);
    },
    changeBackground(newBg) {
      this.changeTextElementStyle("backgroundColor", newBg);
    },
    changeColor(color) {
      this.changeTextElementStyle("color", color);
    },
    changeFont(font) {
      this.changeTextElementStyle("fontSize", `${font}px`);
    },
    copyJSON() {
      copyToClipboard(this.json);
    }
  }
};
</script>

<style scoped lang="scss">
.layout {
  display: flex;
  padding: 30px;
}
.col {
  margin-right: 100px;
}
.text {
  margin: 0;
  max-width: 600px;
  border-radius: 6px;
  line-height: 1.4;
  letter-spacing: 0px;
  font-family: Aleo;
  font-weight: 300;
}
</style>
