<template>
 <div v-if="submission">
    {{ submission.status }}



      
            <sh-icon :name="submission.bookmark ? 'bookmarked-highlight' : 'bookmark'" class="is-18x18" />
 
       </div>   
</template>
<script>
export default {
      props: ["submission"],
}
</script>
<style scoped>

</style>