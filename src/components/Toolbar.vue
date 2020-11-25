<template>
  <v-card class="mx-auto" max-width="60" tile>
    <v-list dense dark nav>
      <v-list-item-group v-model="selectedItem" color="grey lighten-5">
        <v-list-item
          class="my-3"
          inactive
          @keydown.esc="changeMode"
          @click="changeMode"
        >
          <v-icon
            v-text="hand.icon"
            :color="hand.mode ? 'success' : ''"
          ></v-icon>
        </v-list-item>

        <v-divider></v-divider>

        <v-list-item v-for="(item, i) in items" :key="i" :disabled="!hand.mode">
          <v-list-item-icon>
            <v-icon v-text="item.icon" color="grey lighten-1"></v-icon>
          </v-list-item-icon>

          <v-list-item-content> </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    selectedItem: 1,
    hand: { icon: "mdi-cursor-pointer", mode: true, shortKey: "Escape" },

    items: [
      { name: "Select", icon: "mdi-vector-square", shortKey: "1" },
      { name: "Pencil", icon: "mdi-pencil", shortKey: "2" },
      { name: "Magic Pen", icon: "mdi-auto-fix", shortKey: "3" },
      { name: "Brush", icon: "mdi-brush", shortKey: "4" },
      { name: "Eraser", icon: "mdi-eraser", shortKey: "5" },
      { name: "Map", icon: "mdi-map-marker", shortKey: "6" },
      { name: "Crosshairs", icon: "mdi-crosshairs", shortKey: "7" },
    ],
  }),
  created() {
    window.addEventListener("keydown", (e) => {
      if (e.key == this.hand.shortKey) {
        this.changeMode();
      } else {
        this.items.forEach((item) => {
          if (e.key == item.shortKey) {
            this.selectedItem = parseInt(item.shortKey);
          }
        });
      }
    });
  },
  methods: {
    changeMode() {
      this.hand.mode = !this.hand.mode;
    },
  },
};
</script>

