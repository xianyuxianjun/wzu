<script setup>

//学习材料
import { EditorContent } from "@tiptap/vue-3"
import TiptapEditor from "@core/components/TiptapEditor.vue"

const materialsList = ref([
  {
    id : 1,
    title: '学习材料1'
  },
  {
    id : 2,
    title: '学习材料2'
  },
  {
    id : 3,
    title: '学习材料3'
  }
])

//评价标准
const standardList = ref([
  {
    id: 1,
    title: "标准1",
    content:'文字美观',
    score:'25'
  },
  {
    id: 2,
    title: "标准1",
    content:'主题明确',
    score:'25'
  },{
    id: 3,
    title: "标准1",
    content:'论证严谨',
    score:'50'
  }
])

//评价内容
const pj = [
  {
    id:1,
    content:'评价内容1',
  },
  {
    id:2,
    content:'评价内容2',
  },{
    id:3,
    content:'评价内容3',
  },{
    id:4,
    content:'评价内容4',
  },
]
//作业内容
const basicEditorContent = ref('aaaaaaaaaaa')

</script>

<template>
  <VCard>
    <VRow>
      <VCol cols="12" md="2">
        <VCardTitle>
          学习材料
        </VCardTitle>
        <VList rounded="10" v-for="materials in materialsList" :key="materials.id">
          <VListItem>
            <VChip color="primary">
              {{ materials.title }}
            </VChip>
          </VListItem>
        </VList>
        <VCardTitle>
          评价标准
        </VCardTitle>
        <VList v-for="standard in standardList" :key="standard.id">
          <VListItem>
            {{ standard.content }}
            <VChip color="primary">{{ standard.score}}</VChip>
          </VListItem>
        </VList>
      </VCol>
      <VCol cols="12" md="8">
        <VCardTitle>
          作业内容
        </VCardTitle>
        <div>
          <TiptapEditor
            v-model="basicEditorContent"
            class="border rounded"
          />
        </div>
      </VCol>
      <VCol cols="12" md="2">
        <VCardTitle>
          作业反馈
        </VCardTitle>
        <VList>
          <VListItem v-for="p in pj" :key="p.id">
            <template #prepend>
              <VChip>{{ p.id }}</VChip>
            </template>
            <template #default>
              <VListItemSubtitle>{{ p.content }}</VListItemSubtitle>
            </template>
          </VListItem>
          <VCardTitle>
            总体评价
          </VCardTitle>
          <VList>
            <VListItem>
              总分：90
            </VListItem>
            <VListItem>
              总结：做的不错
            </VListItem>
          </VList>
        </VList>
      </VCol>
    </VRow>
  </VCard>
</template>

<style scoped lang="scss">
</style>
