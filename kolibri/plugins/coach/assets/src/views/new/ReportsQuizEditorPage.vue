<template>

  <div class="new-coach-block">
    <QuizDetailEditor />
    <KButton :text="coachStrings.$tr('cancelAction')" :primary="false" />
    <KButton :text="coachStrings.$tr('saveAction')" :primary="true" />
  </div>

</template>


<script>

  import imports from './imports';
  import QuizDetailEditor from './shared/QuizDetailEditor';

  export default {
    name: 'ReportsQuizEditorPage',
    components: {
      QuizDetailEditor,
    },
    mixins: [imports],
    data() {
      return {
        lessonTitle: 'Lesson A',
        lessonDescription: 'Ipsum lorem',
        selectedCollectionIds: ['a'],
        availableGroups: [{ name: 'Group A', id: 'a' }, { name: 'Group B', id: 'b' }],
        selectedClassroomId: 'x',
        isActive: true,
      };
    },
    $trs: {},
  };

</script>


<style lang="scss" scoped></style>
