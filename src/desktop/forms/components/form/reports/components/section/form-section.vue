<template>
  <div>
    <draggable :group="{ name: 'sections' }" :list="sections" handle=".handle" tag="div" @change="checkMove">
      <div v-for="(section, index) in sections" :key="section.uid">
        <section-content :number="index + 1" :sectionLength="sectionLength" :section="section"><slot :type="section"></slot></section-content>
      </div>
    </draggable>
  </div>
</template>

<script>
  import sectionContent from "./components/section-content";
  import { mapMutations, mapState, mapGetters, mapActions } from "vuex";
  import draggable from "vuedraggable";

  export default {
    props: ["sections"],
    components: { sectionContent, draggable },
    computed: {
      sectionLength(){
        return this.sections.length;
      },
    },
    methods: {
      ...mapActions("forms", ["delete_section", "update_section"]),
      updateSection(section) {
        this.update_section({
          id: section.uid,
          body: section,
        });
      },
      checkMove(data) {
        if (data.moved.newIndex - 1 >= 0) {
          this.sections[data.moved.newIndex].previousSection = this.sections[data.moved.newIndex - 1].uid;
        } else {
          this.sections[data.moved.newIndex].previousSection = null;
        }
        this.updateSection(this.sections[data.moved.newIndex]);
      },
    },
  };
</script>
