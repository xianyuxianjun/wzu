<script setup>
import { ref } from 'vue'

//搜索框的值
const search = ref('')

//表格的表头
const headers = [
  {
    title: '作业名称',
    key: 'name',
  },
  {
    title: '教师',
    key: 'teacher',
  },
  {
    title: '发布时间',
    key: 'publishTime',
  },

  {
    title: '截止时间',
    key: 'deadline',
  },
  {
    title: '状态',
    key: 'status',
  },
]

//表格的数据
const myAllHomeworkData = ref([
  {
    name: '作业1',
    teacher: '张三',
    publishTime: '2021-09-01',
    deadline: '2021-09-10',
    status: '未完成',
  },
  {
    name: '作业2',
    teacher: '李四',
    publishTime: '2021-09-02',
    deadline: '2021-09-11',
    status: '已完成',
  },
  {
    name: '作业3',
    teacher: '王五',
    publishTime: '2021-09-03',
    deadline: '2021-09-12',
    status: '未完成',
  },
  {
    name: '作业4',
    teacher: '赵六',
    publishTime: '2021-09-04',
    deadline: '2021-09-13',
    status: '已完成',
  },
  {
    name: '作业5',
    teacher: '孙七',
    publishTime: '2021-09-05',
    deadline: '2021-09-14',
    status: '未完成',
  },
])

//展示的数据
const myHomeworkData = ref(myAllHomeworkData.value)

//搜索
const searchHomework = () => {
  const searchData = myAllHomeworkData.value.filter(item => item.name === search.value)
  console.log(searchData)
  myHomeworkData.value = searchData
}

//选择框
const selectValueList = [
  {
    title: '全部',
    value: '全部',
  },
  {
  title: '未完成',
  value: '未完成',
},
{
  title: '已完成',
  value: '已完成',
}]

//选择框的值
const selectValue = ref('全部')
//选择之后
const selectFunction = () => {
  if (selectValue.value === '全部') {
    myHomeworkData.value = myAllHomeworkData.value;
  } else {
    myHomeworkData.value = myAllHomeworkData.value.filter(item => item.status === selectValue.value);
  }
}
</script>

<template>
  <VCard title="我的作业" style="height: 83vh;">
    <VCardText>
      <VRow justify="end" class="mb-4">
        <VCol cols="12" md="2">
          <VSelect label="请选择" :items="selectValueList" v-model="selectValue" @update:model-value=selectFunction ></VSelect>
        </VCol>
        <VCol cols="12" md="2">
          <VTextField v-model="search" label="搜索" placeholder="搜索" prepend-inner-icon="ri-search-line" @keyup.enter="searchHomework"></VTextField>
        </VCol>
      </VRow>
      <VDataTable :headers="headers" :items="myHomeworkData" style="height: 67vh">
          <template #item.status="{ item }">
            <VChip v-if="item.status === '未完成'" color="error">未完成</VChip>
            <VChip v-else color="success">已完成</VChip>
          </template>
      </VDataTable>
    </VCardText>
  </VCard>
</template>

<style scoped lang="scss">

</style>
