<template>

  <KModal
    :title="$tr('title')"
    :submitText="$tr('confirmButtonLabel')"
    :cancelText="$tr('cancelButtonLabel')"
    @submit="handleClickConfirm"
    @cancel="handleClickCancel"
  >
    <p>{{ $tr('confirmationQuestion', { channelTitle }) }}</p>
  </KModal>

</template>


<script>

  import KModal from 'kolibri.coreVue.components.KModal';

  export default {
    name: 'DeleteChannelModal',
    components: {
      KModal,
    },
    props: {
      channelTitle: {
        type: String,
        required: true,
      },
    },
    methods: {
      handleClickCancel() {
        this.$emit('cancel');
      },
      handleClickConfirm() {
        this.$emit('confirm');
      },
    },
    $trs: {
      confirmationQuestion: `Are you sure you want to delete '{ channelTitle }' from your device?`,
      title: 'Delete channel',
      cancelButtonLabel: 'Cancel',
      confirmButtonLabel: 'Delete',
    },
  };

</script>


<style lang="scss" scoped></style>
