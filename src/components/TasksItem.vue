<template>
  <div class="task-item">
    <label class="item" :class="{ done: task.isCompleted }" :for="task.id">{{
      task.title
    }}</label>
    <div class="checkbox-wrapper-12">
      <div class="cbx">
        <input
          :id="task.id"
          type="checkbox"
          :checked="task.isCompleted"
          @change="
            $emit('update:model-value', $event.target.checked),
              $emit('updateLocalStorage', task)
          " />
        <label :for="task.id"></label>
        <svg width="15" height="14" viewbox="0 0 15 14" fill="none">
          <path d="M2 8.36364L6.23077 12L13 2"></path>
        </svg>
      </div>
    </div>
    <button class="button-45" role="button" @click="$emit('removeItem', task)">
      x
    </button>
  </div>
</template>

<script>
export default {
  props: {
    task: Object,
    modelValue: Boolean,
  },
};
</script>

<style>
.task-item {
  display: flex;
}
.task-item .item {
  font-size: 1.2em;
  margin-bottom: 30px;
  text-transform: capitalize;
  width: 100%;
  cursor: pointer;
}

.checkbox-wrapper-12 {
  position: relative;
  margin-right: 10px;
}
.checkbox-wrapper-12 > svg {
  position: absolute;
  top: -130%;
  left: -170%;
  width: 110px;
  pointer-events: none;
}
.checkbox-wrapper-12 * {
  box-sizing: border-box;
}
.checkbox-wrapper-12 input[type="checkbox"] {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  -webkit-tap-highlight-color: transparent;
  cursor: pointer;
  margin: 0;
}
.checkbox-wrapper-12 input[type="checkbox"]:focus {
  outline: 0;
}
.checkbox-wrapper-12 .cbx {
  width: 24px;
  height: 24px;
  top: calc(50vh - 12px);
  left: calc(50vw - 12px);
}
.checkbox-wrapper-12 .cbx input {
  position: absolute;
  top: 0;
  left: 0;
  width: 24px;
  height: 24px;
  border: 2px solid #bfbfc0;
  border-radius: 50%;
}
.checkbox-wrapper-12 .cbx label {
  width: 24px;
  height: 24px;
  background: none;
  border-radius: 50%;
  position: absolute;
  top: 0;
  left: 0;
  -webkit-filter: url("#goo-12");
  filter: url("#goo-12");
  transform: trasnlate3d(0, 0, 0);
  pointer-events: none;
}
.checkbox-wrapper-12 .cbx svg {
  position: absolute;
  top: 5px;
  left: 4px;
  z-index: 1;
  pointer-events: none;
}
.checkbox-wrapper-12 .cbx svg path {
  stroke: #fff;
  stroke-width: 3;
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-dasharray: 19;
  stroke-dashoffset: 19;
  transition: stroke-dashoffset 0.3s ease;
  transition-delay: 0.2s;
}
.checkbox-wrapper-12 .cbx input:checked + label {
  animation: splash-12 0.6s ease forwards;
}
.checkbox-wrapper-12 .cbx input:checked + label + svg path {
  stroke-dashoffset: 0;
}
@-moz-keyframes splash-12 {
  40% {
    background: #50e3a4;
    box-shadow: 0 -18px 0 -8px #50e3a4, 16px -8px 0 -8px #50e3a4,
      16px 8px 0 -8px #50e3a4, 0 18px 0 -8px #50e3a4, -16px 8px 0 -8px #50e3a4,
      -16px -8px 0 -8px #50e3a4;
  }
  100% {
    background: #50e3a4;
    box-shadow: 0 -36px 0 -10px transparent, 32px -16px 0 -10px transparent,
      32px 16px 0 -10px transparent, 0 36px 0 -10px transparent,
      -32px 16px 0 -10px transparent, -32px -16px 0 -10px transparent;
  }
}
@-webkit-keyframes splash-12 {
  40% {
    background: #50e3a4;
    box-shadow: 0 -18px 0 -8px #50e3a4, 16px -8px 0 -8px #50e3a4,
      16px 8px 0 -8px #50e3a4, 0 18px 0 -8px #50e3a4, -16px 8px 0 -8px #50e3a4,
      -16px -8px 0 -8px #50e3a4;
  }
  100% {
    background: #50e3a4;
    box-shadow: 0 -36px 0 -10px transparent, 32px -16px 0 -10px transparent,
      32px 16px 0 -10px transparent, 0 36px 0 -10px transparent,
      -32px 16px 0 -10px transparent, -32px -16px 0 -10px transparent;
  }
}
@-o-keyframes splash-12 {
  40% {
    background: #50e3a4;
    box-shadow: 0 -18px 0 -8px #50e3a4, 16px -8px 0 -8px #50e3a4,
      16px 8px 0 -8px #50e3a4, 0 18px 0 -8px #50e3a4, -16px 8px 0 -8px #50e3a4,
      -16px -8px 0 -8px #50e3a4;
  }
  100% {
    background: #50e3a4;
    box-shadow: 0 -36px 0 -10px transparent, 32px -16px 0 -10px transparent,
      32px 16px 0 -10px transparent, 0 36px 0 -10px transparent,
      -32px 16px 0 -10px transparent, -32px -16px 0 -10px transparent;
  }
}
@keyframes splash-12 {
  40% {
    background: #50e3a4;
    box-shadow: 0 -18px 0 -8px #50e3a4, 16px -8px 0 -8px #50e3a4,
      16px 8px 0 -8px #50e3a4, 0 18px 0 -8px #50e3a4, -16px 8px 0 -8px #50e3a4,
      -16px -8px 0 -8px #50e3a4;
  }
  100% {
    background: #50e3a4;
    box-shadow: 0 -36px 0 -10px transparent, 32px -16px 0 -10px transparent,
      32px 16px 0 -10px transparent, 0 36px 0 -10px transparent,
      -32px 16px 0 -10px transparent, -32px -16px 0 -10px transparent;
  }
}

.button-45 {
  width: 30.3px;
  height: 25px;
  align-items: center;
  background-color: #ffe7e7;
  background-position: 0 0;
  border: 1px solid #fee0e0;
  border-radius: 50%;
  box-sizing: border-box;
  color: #d33a2c;
  cursor: pointer;
  display: flex;
  justify-content: center;
  font-size: 1rem;
  font-weight: 700;
  list-style: outside url(https://www.smashingmagazine.com/images/bullet.svg)
    none;
  transition: border 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
  word-break: break-word;
}
.button-45:active,
.button-45:hover,
.button-45:focus {
  outline: 0;
}

.button-45:hover {
  background-color: #ffe3e3;
  border-color: #faa4a4;
}
.button-45:active:hover {
  background-color: #d33a2c;
  box-shadow: rgba(0, 0, 0, 0.12) 0 1px 3px 0 inset;
  color: #ffffff;
}

.done {
  opacity: 50%;
  transition: 0.3s;
  text-decoration: line-through;
}
</style>
