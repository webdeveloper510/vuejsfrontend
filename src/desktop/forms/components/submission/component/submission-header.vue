<template>
  <div class="columns is-mobile has-text-centered is-normal-14-500-17 has-text-theme-grey py-10">
    <div class="column is-1 mr-10"></div>
    <div @click="update_sort_key('forms')" class=" column is-3 mr-15 is-flex is-vcenter">
      <span class="is-pointer">
        Forms
      </span>

      <span class="sort-indicators">
        <i class="fas fa-chevron-up fa-xs header-sort-icon" :class="[sorting_key === 'forms' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
        <i class="fas fa-chevron-down fa-xs header-sort-icon" :class="[sorting_key === '-forms' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
      </span>
    </div>
    <div @click="update_sort_key('invited')" class="column is-1 is-flex is-vcenter" :class="{ null: !small_viewer }">
      <span class="is-pointer">
        Invited By
      </span>

      <span class="sort-indicators">
        <i class="fas fa-chevron-up fa-xs header-sort-icon" :class="[sorting_key === 'invited' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
        <i class="fas fa-chevron-down fa-xs header-sort-icon" :class="[sorting_key === '-invited' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
      </span>
    </div>
    <div @click="update_sort_key('duedate')" class=" column is-flex is-vcenter is-center ml-10" :class="[small_viewer ? 'is-4' : 'is-3']">
      <span class="is-pointer">Due date</span>
      <span class="sort-indicators">
        <i class="fas fa-chevron-up fa-xs header-sort-icon" :class="[sorting_key == 'duedate' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
        <i class="fas fa-chevron-down fa-xs header-sort-icon" :class="[sorting_key == '-duedate' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
      </span>
    </div>

    <div
      @click="update_sort_key('status')"
      class=" column is-flex is-vcenter is-1 mr-50"
      style="margin-left: -.4rem;"
      :class="[small_viewer ? 'ml-20' : null]"
    >
      <span class="is-pointer">Status</span>
      <span class="sort-indicators">
        <i class="fas fa-chevron-up fa-xs header-sort-icon" :class="[sorting_key === 'status' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
        <i class="fas fa-chevron-down fa-xs header-sort-icon" :class="[sorting_key === '-status' ? 'has-text-blue' : 'has-text-theme-grey']"></i>
      </span>
    </div>

  </div>
</template> 
<script>
  export default {
    props: ["sorting_key", "small_viewer"],
    methods: {
      update_sort_key(value) {
        let new_value;
        this.sorting_key == value ? (new_value = "-" + value) : (new_value = value);
        this.$emit("update_sort_key", new_value);
      },
    },
  };
</script>
<style lang="scss">
  .header-sort-icon {
    cursor: pointer;
    height: 4px;
    width: 12px;
    margin: -2px 3px;
    display: table;
    font-weight: 600;
    font-size: 8px;
  }
</style>