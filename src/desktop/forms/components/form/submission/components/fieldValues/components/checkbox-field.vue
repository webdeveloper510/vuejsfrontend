<template>
  <div class="email">
    <div class="columns"></div>
    <div v-for="(item, i) in items" :key="item" class="is-flex is-vcenter mt-15 ml-15">
      <input class="sh-custom-checkbox is-thinner fill" :name="item + i" type="checkbox" />
      <label class="ml-10" :for="item + i">{{ item }}</label>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        id: 0,
        items: ["Red", "Blue", "Green"],
      };
    },
    methods: {
      addOption() {
        this.id++;
        this.items.push({ tyep: "checkbox", icon: false, id: this.id });
        console.log(this.items);
      },
      showIcon(id) {
        for (var i = 0; i < this.items.length; i++) {
          this.items[i].icon = false;
        }
        for (var i = 0; i < this.items.length; i++) {
          if (this.items[i].id == id) {
            this.items[i].icon = true;
          }
        }
      },
      clearIcon() {
        for (var i = 0; i < this.items.length; i++) {
          this.items[i].icon = false;
        }
      },
      delElement(id) {
        for (var i = 0; i < this.items.length; i++) {
          if (this.items[i].id == id) {
            this.items.splice(i, 1);
          }
        }
      },
    },
  };
</script>

<style scoped>
  .add {
    cursor: pointer;
  }
  .border {
    border-top: 1px dashed #000;
  }
  .middlesub {
    display: flex;
    align-items: center;
  }
  .subArrange {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 30%;
  }
  .subArrange1 {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-top: 10px;
  }
  .arrange {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 40%;
    margin-left: 10px;
    padding-bottom: 20px;
  }
  .imgSize {
    width: 10px !important;
    cursor: pointer;
  }
  .flexEnd {
    display: flex;
    align-items: flex-end;
  }
  .email {
    background: white;
    margin-left: 15px;
    box-sizing: border-box;
  }
  .title {
    border-bottom: 1px dashed #5b607e;
    opacity: 1;
    width: 300px;
  }
  #input {
    border: 0px;
    box-shadow: none;
    padding: 2px;
  }
  .column {
    padding: 20px;
  }
  .text {
    position: absolute;
    margin-left: 5px;
    display: inline;
  }
  img {
    width: 24px;
    height: 24px;
  }
</style>
