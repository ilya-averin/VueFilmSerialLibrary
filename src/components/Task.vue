<template lang="pug">
  .content-wrapper
    section
      .container
        h1.ui-title-2 Tasks
        .task-list
          .task-item(
            v-for="task in tasks"
            :key="task.id"
            :class="{ completed: task.completed }"
          )
            .ui-card.ui-card--shadow
              .task-item__info
                .task-item__main-info
                  span.ui-label.ui-label--light {{ task.whatWatch }}
                  span Total Time:
                span.button-close
              .task-item__content
                .task-item__header
                  .ui-checkbox-wrapper
                      input.ui-checkbox(
                        type='checkbox'
                        v-model="task.completed"
                      )
                  span.ui-title-3 {{ task.title }}
                .task-item__body
                  p.ui-text-regular {{ task.description }}
</template>

<script>
export default {
  computed: {
    tasks() {
      return this.$store.getters.tasks
    }
  }
}
</script>

<style lang="stylus" scoped>

.task-item
    // margin-top 20px
    margin-bottom 20px
    &:last-child
      margin-bottom 0

.ui-label
    margin-right 8px
    border-radius 3px
    // background-color blue

.task-item__info
    display flex
    align-items center
    justify-content space-between
    margin-bottom  20px
.button-close
    width 20px
    height @width

.task-item__header
    display flex
    align-items center
    margin-bottom 10px

.ui-checkbox-wrapper
    margin-right 10px

.ui-title-3
    margin-bottom -5px

</style>
