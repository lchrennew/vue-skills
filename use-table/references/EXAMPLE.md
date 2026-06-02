```vue
<template>
  <a-table :data-source="dataSource">
    <a-table-column-group>
      <template #title><span class="group-title">Name Info</span></template>
      <a-table-column title="First Name" data-index="firstName" />
      <a-table-column title="Last Name" data-index="lastName" />
    </a-table-column-group>
    
    <a-table-column title="Age" data-index="age" />
    <a-table-column title="Address" data-index="address" />
    
    <a-table-column title="Tags" data-index="tags" #="{ text: tags }">
        <!-- IMPORTANT: v-for without key attribute -->
        <a-tag v-for="tag in tags" color="blue">
          {{ tag }}
        </a-tag>
    </a-table-column>
    
    <a-table-column title="Action" #="{ record }">
        <a>Invite {{ record.firstName }}</a>
        <a-divider type="vertical" />
        <a>Delete</a>
    </a-table-column>
  </a-table>
</template>

<script setup>
import { ref } from 'vue';

const dataSource = ref([
  {
    firstName: 'John',
    lastName: 'Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    tags: ['nice', 'developer'],
  },
  {
    firstName: 'Jim',
    lastName: 'Green',
    age: 42,
    address: 'London No. 1 Lake Park',
    tags: ['loser'],
  },
]);
</script>

<style lang="less" scoped>
.group-title {
  color: #1890ff;
}
</style>
```