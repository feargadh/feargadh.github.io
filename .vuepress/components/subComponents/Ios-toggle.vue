<template>
  <div class="toggler" :style="{...buttonSizeStyles }">
    <label>
      <input type="checkbox"/>
      <span></span>
    </label>
    <strong>
      <!-- <slot/>为父组件调用子组件的标签内的内容 -->
      <slot/>
    </strong>
  </div>
</template>

<script>
export default {
  props: {
    size: {
      type: Number,
      default: 1
    }
  },
  data() {
    return {
      buttonWdith: 50,
      buttonHeight: 30,
      toggleDiameter: 26,
      toggleWider: 34
    };
  },
  computed: {
    buttonSizeStyles() {
      return {
        "--button-width": this.buttonWdith * this.size + "px",
        "--button-height": this.buttonHeight * this.size + "px",
        "--toggle-diameter": this.toggleDiameter * this.size + "px",
        "--toggle-wider": this.toggleWider * this.size + "px"
      };
    }
  }
};
</script>

<style scoped>
.toggler {
  --button-width: 500px;
  --button-height: 295px;
  --toggle-diameter: 255px;
  --toggle-wider: 333px;

  --button-toggle-offset: calc(
    (var(--button-height) - var(--toggle-diameter)) / 2
  );
  --toggle-shadow-offset: 10px;
  --color-grey: #e9e9ea;
  --color-dark-grey: #39393d;
  --color-green: #30d158;
}

span {
  display: inline-block;
  width: var(--button-width);
  height: var(--button-height);
  background-color: var(--color-dark-grey);
  border-radius: calc(var(--button-height) / 2);
  position: relative;
  transition: 0.3s all ease-in-out;
}

span:after {
  content: "";
  display: inline-block;
  width: var(--toggle-diameter);
  height: var(--toggle-diameter);
  background-color: #fff;
  border-radius: calc(var(--toggle-diameter) / 2);
  position: absolute;
  top: var(--button-toggle-offset);
  left: 0;
  transform: translateX(var(--button-toggle-offset));
  box-shadow: var(--toggle-shadow-offset) 0
    calc(var(--toggle-shadow-offset) * 4) rgba(0, 0, 0, 0.1);
  transition: 0.3s all ease-in-out;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #1c1c1e;
}

input[type="checkbox"]:checked + span {
  background-color: var(--color-green);
}

input[type="checkbox"]:checked + span::after {
  transform: translateX(
    calc(
      var(--button-width) - var(--toggle-diameter) - var(--button-toggle-offset)
    )
  );
  box-shadow: calc(var(--toggle-shadow-offset) * -1) 0
    calc(var(--toggle-shadow-offset) * 4) rgba(0, 0, 0, 0.1);
}

input[type="checkbox"] {
  display: none;
}

input[type="checkbox"]:active + span::after {
  width: var(--toggle-wider);
}

input[type="checkbox"]:checked:active + span::after {
  transform: translateX(
    calc(
      var(--button-width) - var(--toggle-wider) - var(--button-toggle-offset)
    )
  );
}

.toggler{
  display:inline-flex;
  flex-direction: row;
}

.toggler strong{
  line-height:var(--button-height);
  font-size: var(--toggle-diameter);
  margin: calc(var(--toggle-diameter)/4);
  color: #fff;
}
</style>