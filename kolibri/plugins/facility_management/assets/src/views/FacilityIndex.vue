<template>

  <CoreBase
    :appBarTitle="appBarTitle"
    :immersivePage="isImmersive"
    immersivePageIcon="arrow_back"
    :immersivePageRoute="appBarBackLink"
    :immersivePagePrimary="true"
    :authorized="userIsAuthorized"
    :authorizationErrorDetails="$tr('adminOrSuperuser')"
    :showSubNav="userIsAuthorized && !isEnrollmentPage"
  >
    <FacilityTopNav slot="sub-nav" />

    <div class="facility-management">
      <!-- QUESTION should we explicitly define this in every page? -->
      <component :is="currentPage" />
    </div>

  </CoreBase>

</template>


<script>

  import { mapState, mapGetters } from 'vuex';
  import CoreBase from 'kolibri.coreVue.components.CoreBase';
  import { PageNames } from '../constants';
  import ClassEditPage from './ClassEditPage';
  import CoachClassAssignmentPage from './CoachClassAssignmentPage';
  import LearnerClassEnrollmentPage from './LearnerClassEnrollmentPage';
  import DataPage from './DataPage';
  import FacilitiesConfigPage from './FacilityConfigPage';
  import ManageClassPage from './ManageClassPage';
  import FacilityTopNav from './FacilityTopNav';
  import UserPage from './UserPage';

  const classEnrollmentPages = [PageNames.CLASS_ENROLL_LEARNER, PageNames.CLASS_ASSIGN_COACH];

  const pageNameComponentMap = {
    [PageNames.CLASS_EDIT_MGMT_PAGE]: ClassEditPage,
    [PageNames.CLASS_MGMT_PAGE]: ManageClassPage,
    [PageNames.CLASS_ENROLL_LEARNER]: LearnerClassEnrollmentPage,
    [PageNames.CLASS_ASSIGN_COACH]: CoachClassAssignmentPage,
    [PageNames.DATA_EXPORT_PAGE]: DataPage,
    [PageNames.FACILITY_CONFIG_PAGE]: FacilitiesConfigPage,
    [PageNames.USER_MGMT_PAGE]: UserPage,
  };

  export default {
    $trs: {
      facilityTitle: 'Facility',
      adminOrSuperuser: 'You must be signed in as an admin or super admin to view this page',
      // here because going to use immersive-page
      detailPageReturnPrompt: 'Class details',
    },
    name: 'FacilityIndex',
    components: {
      CoreBase,
      FacilityTopNav,
    },
    computed: {
      ...mapGetters(['isAdmin', 'isSuperuser']),
      ...mapState(['pageName']),
      isEnrollmentPage() {
        return classEnrollmentPages.includes(this.pageName);
      },
      currentPage() {
        return pageNameComponentMap[this.pageName] || null;
      },
      userIsAuthorized() {
        return this.isAdmin || this.isSuperuser;
      },
      appBarTitle() {
        if (this.isEnrollmentPage) {
          return this.$tr('detailPageReturnPrompt');
        }
        return this.$tr('facilityTitle');
      },
      appBarBackLink() {
        if (this.isEnrollmentPage) {
          return {
            name: PageNames.CLASS_EDIT_MGMT_PAGE,
          };
        }
        return null;
      },
      isImmersive() {
        return this.isEnrollmentPage;
      },
    },
  };

</script>


<style lang="scss" scoped></style>
