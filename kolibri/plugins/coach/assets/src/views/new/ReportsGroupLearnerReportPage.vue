<template>

  <div class="new-coach-block">

    <ReportsGroupLearnerHeader />

    <KGrid>
      <KGridItem :sizes="[100, 100, 50]" percentage>
        <h2>{{ coachStrings.$tr('lessonsAssignedLabel') }}</h2>
        <table class="new-coach-table">
          <thead>
            <tr>
              <td>{{ coachStrings.$tr('titleLabel') }}</td>
              <td>{{ coachStrings.$tr('progressLabel') }}</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <KRouterLink
                  :to="newCoachRoute('ReportsGroupLearnerReportLessonPage')"
                  text="Some lesson"
                />
              </td>
              <td>
                <LearnerProgressLabel
                  :verbosity="1"
                  :count="1"
                  verb="notStarted"
                  icon="nothing"
                />
              </td>
            </tr>
            <tr>
              <td>
                <KRouterLink
                  :to="newCoachRoute('ReportsGroupLearnerReportLessonPage')"
                  text="Another lesson"
                />
              </td>
              <td>
                <LearnerProgressLabel
                  :verbosity="1"
                  :count="1"
                  verb="needHelp"
                  icon="help"
                />
              </td>
            </tr>
            <tr>
              <td>
                <KRouterLink
                  :to="newCoachRoute('ReportsGroupLearnerReportLessonPage')"
                  text="Lesson 1"
                />
              </td>
              <td>
                <LearnerProgressLabel
                  :verbosity="1"
                  :count="1"
                  verb="completed"
                  icon="star"
                />
              </td>
            </tr>
            <tr>
              <td>
                <KRouterLink
                  :to="newCoachRoute('ReportsGroupLearnerReportLessonPage')"
                  text="Lesson 2"
                />
              </td>
              <td>
                <LearnerProgressLabel
                  :verbosity="1"
                  :count="1"
                  verb="started"
                  icon="clock"
                />
              </td>
            </tr>
          </tbody>
        </table>
      </KGridItem>
      <KGridItem :sizes="[100, 100, 50]" percentage>
        <h2>{{ coachStrings.$tr('quizzesAssignedLabel') }}</h2>
        <table class="new-coach-table">
          <thead>
            <tr>
              <td>{{ coachStrings.$tr('titleLabel') }}</td>
              <td>{{ coachStrings.$tr('progressLabel') }}</td>
              <td>{{ coachStrings.$tr('scoreLabel') }}</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <KRouterLink
                  :to="newCoachRoute('ReportsGroupLearnerReportQuizPage')"
                  text="Some quiz"
                />
              </td>
              <td>
                <LearnerProgressLabel
                  :verbosity="1"
                  :count="1"
                  verb="completed"
                  icon="star"
                />
              </td>
              <td><Score :value="0.92" /></td>
            </tr>
            <tr>
              <td>
                <KRouterLink
                  :to="newCoachRoute('ReportsGroupLearnerReportQuizPage')"
                  text="Another quiz"
                />
              </td>
              <td>
                <LearnerProgressLabel
                  :verbosity="1"
                  :count="1"
                  verb="started"
                  icon="clock"
                />
              </td>
              <td><Score /></td>
            </tr>
          </tbody>
        </table>
      </KGridItem>
    </KGrid>

  </div>

</template>


<script>

  import imports from './imports';
  import ReportsGroupLearnerHeader from './ReportsGroupLearnerHeader';

  export default {
    name: 'ReportsGroupLearnerReportPage',
    components: {
      ReportsGroupLearnerHeader,
    },
    mixins: [imports],
    $trs: {},
  };

</script>


<style lang="scss" scoped>

  .new-coach-table {
    min-width: 0;
  }

</style>
