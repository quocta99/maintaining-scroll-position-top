<template>
  <div>
    <button @click="handleUnshift">Unshift</button>
    <div class="viewport" ref="viewport">
      <div :style="item" v-for="(item, index) in items" :key="index">
        {{ items.length - index }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      items: [],
    };
  },
  mounted() {
    this.items = [
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
      this.randBackColor(),
    ];
  },
  methods: {
    randBackColor() {
      return {
        backgroundColor: "hsl( 0, 100%, " + Math.random() * 100 + "% )",
      };
    },
    handleUnshift() {
      const note = this.$refs.viewport;

      const previousScrollHeightMinusTop = note.scrollHeight - note.scrollTop;

      this.items = [
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        this.randBackColor(),
        ...this.items,
      ];

      setTimeout(() => {
        this.$refs.viewport.scrollTop =
          this.$refs.viewport.scrollHeight - previousScrollHeightMinusTop;
      }, 1);
    },
  },
};
</script>

<style>
html,
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  height: 100%;
}
.viewport {
  height: 300px;
  overflow-y: scroll;
  border: 1px solid hsl(0, 100%, 5%);
}
.viewport div {
  height: 40px;
  color: white;
}
</style>
