<template>
    <div class="content">
        <el-row class="dr-datatable">
            <el-col :span="24">
                <TopBar type="content" :ids="selectlist" :pageInfo="contentList.pageInfo"></TopBar>
                <DataTable :dataList="contentList.docs" :pageInfo="contentList.pageInfo" @changeContentSelectList="changeSelect"></DataTable>
                <Pagination :pageInfo="contentList.pageInfo" pageType="content"></Pagination>
            </el-col>
        </el-row>
    </div>
</template>
<script>
import DataTable from "./dataTable.vue";
import TopBar from "../common/TopBar.vue";
import Pagination from "../common/Pagination.vue";
import { mapGetters, mapActions } from "vuex";

export default {
  name: "index",
  data() {
    return {
      selectlist: []
    };
  },
  components: {
    DataTable,
    TopBar,
    Pagination
  },
  methods: {
    changeSelect(ids) {
      this.selectlist = ids;
    }
  },
  computed: {
    ...mapGetters(["contentList"])
  },
  mounted() {
    this.$store.dispatch("getContentList");
  }
};
</script>

<style lang="">

</style>