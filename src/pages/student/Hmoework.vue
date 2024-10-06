<script setup>

//学习材料
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

//评分细则
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

const homework = ref({
  title:"操作系统第一次作业",
  content:"课本第666页第33题，写完拍照上传",
  date:'2024-1-1'
})

const basicEditorContent = ref('')
</script>

<template>
  <VCard>
    <template #append>
      <VBtn class="me-2">保存</VBtn>
      <VBtn color="success">提交</VBtn>
    </template>
    <VCardText>
      <VRow>
        <VCol cols="12" md="2">
          <VCardTitle>学习材料</VCardTitle>
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
        <VCol cols="12" md="10">
          <VRow>
              <VCardTitle>
                {{ homework.title }}
              </VCardTitle>
          </VRow>
          <VRow>
            <VCardText>
              {{ homework.content }}
            </VCardText>
          </VRow>
          <VRow>
            <VCardText>
              <VChip color="success">{{ homework.date }}截止</VChip>
            </VCardText>
          </VRow>
          <div>
            <TiptapEditor
              v-model="basicEditorContent"
              class="border rounded"
              style="height: 60vh"
            />
          </div>
        </VCol>
      </VRow>
    </VCardText>
  </VCard>
</template>

<style lang="scss">
.ProseMirror {
  block-size: 200px;
  outline: none;
  overflow-y: auto;
  padding-inline: 0.5rem;
}
</style>
