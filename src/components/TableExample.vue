<template>
  <a-table
    :columns="columns"
    :row-key="(record) => record.group_id"
    :data-source="dataSource"
    :pagination="pagination"
    :loading="loading"
    @change="handleTableChange"
  >
    <template #name="{ text }">{{ text.first }} {{ text.last }}</template>
  </a-table>
</template>
<script>
import { usePagination } from "vue-request";
import { computed, defineComponent } from "vue";
const columns = [
  {
    title: "Group Name",
    dataIndex: "name",
    // sorter: true,
    width: "20%",
    // slots: {
    //   customRender: "name",
    // },
  },
  {
    title: "Group ID",
    dataIndex: "group_id",
    // filters: [
    //   {
    //     text: "Male",
    //     value: "male",
    //   },
    //   {
    //     text: "Female",
    //     value: "female",
    //   },
    // ],
    width: "20%",
  },
  {
    title: "Source",
    dataIndex: "source",
  },
];

const queryData = (params) => {
  return `http://127.0.0.1:5000/api/v1/enterprise/groups?${new URLSearchParams(
    params
  )}`;
};

export default defineComponent({
  setup() {
    const {
      data: dataSource,
      run,
      loading,
      current,
      pageSize,
    } = usePagination(queryData, {
      formatResult: (res) => res.data,
      pagination: {
        currentKey: "offset",
        pageSizeKey: "limit",
      },
    });
    const pagination = computed(() => ({
      total: 200,
      current: current.value / pageSize.value + 1,
      pageSize: pageSize.value,
    }));

    const handleTableChange = (pag, filters, sorter) => {
      run({
        offset: (pag?.current - 1) * pag.pageSize,
        limit: pag.pageSize,
        ...filters,
      });
    };

    return {
      dataSource,
      pagination,
      loading,
      columns,
      handleTableChange,
    };
  },
});
</script>
