<template>
  <div class="singer" v-loading="!singers.length">
    <index-list :data="singers"></index-list>
  </div>
</template>

<script>
import { getSingerList } from '@/service/singer';
import IndexList from '@/components/index-list/index-list';
export default {
  name: 'singer',
  components: {
    IndexList
  },
  data() {
    return {
      singers: [],
      selectedSinger: null
    };
  },
  async created() {
    const result = await getSingerList();
    this.singers = result.singers;
  },
  methods: {}
};
</script>

<style lang="scss" scope>
.singer {
  position: fixed;
  width: 100%;
  top: 88px;
  bottom: 0;
}
</style>
