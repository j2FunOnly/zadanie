<template>
  <div class="toolbar">
    <div class="pickers">
      <label class="picker">
        <div class="label">Выбрать цвет</div>
        <input type="color" name="color" v-model="color" />
      </label>

      <label class="picker">
        <div class="label">Выбрать размер шрифта</div>
        <input type="number" name="font" v-model="fontSize" />
      </label>
    </div>

    <div class="buttons">
      <Button @click="changeColor">
        Изменить цвет текста
      </Button>

      <Button @click="changeBackground">
        Изменить цвет фона
      </Button>

      <Button @click="changeFontSize">
        Изменить размер шрифта
      </Button>
    </div>
  </div>
</template>

<script>
import Button from "./Button";

/**
 * Toolbar to pick font size and color
 * @param {boolean} disabled - is apply buttons disabled
 * @event 'change-font' - triggers when apply font button clicked, have new fontSize as
 * first argument
 * @event 'change-bg' - triggers when apply background button clicked, have new color as
 * first argument
 * @event 'change-color' - triggers when apply color button clicked, have new color as
 * first argument
 */
export default {
  components: {
    Button
  },
  data() {
    return {
      fontSize: "14",
      color: "#000000"
    };
  },
  methods: {
    changeFontSize() {
      this.toggle("change-font", this.fontSize);
    },
    changeBackground() {
      this.toggle("change-bg", this.color);
    },
    changeColor() {
      this.toggle("change-color", this.color);
    }
  }
};
</script>

<style scoped lang="scss">
.pickers {
  display: flex;
  margin-bottom: 10px;
}

.picker {
  margin-right: 20px;

  input {
    font-size: 16px;
    max-width: 120px;
  }
}

.label {
  margin-bottom: 5px;
}
</style>
