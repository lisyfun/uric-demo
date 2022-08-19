<template>
  <div class="table-box">
    <!--    title    -->
    <div class="table-title">
      <h2>最简单的CRUD</h2>
    </div>
    <!--    功能区   -->
    <div class="query-box">
      <el-input
          v-model="queryInput"
          class="query-input"
          placeholder="请输入姓名"
          :suffix-icon="Search"
          clearable
      />
      <el-button type="primary" @click="addForm">新增</el-button>
    </div>
    <!--  table-box -->
    <div class="table-body">
      <el-table
          ref="multipleTableRef"
          :data="tableData"
          style="width: 100%"
          @selection-change="handleSelectionChange"
          border
      >
        <el-table-column fixed type="selection" width="55"/>
        <el-table-column prop="name" label="姓名" width="120"/>
        <el-table-column prop="phone" label="电话" width="120"/>
        <el-table-column prop="email" label="邮箱" width="120"/>
        <el-table-column prop="address" label="地址" width="600"/>
        <el-table-column prop="status" label="状态" width="120"/>
        <el-table-column fixed="right" label="操作" width="120">
          <template #default>
            <el-button link type="primary" size="small" @click="editForm">编辑</el-button>
            <el-button link type="primary" size="small" @click="handleClick" style="color: #F56C6C">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>


  <div class="form-box">

    <el-dialog v-model="dialogFormVisible" title="Shipping address">
      <el-form :model="tableForm">
        <el-form-item label="姓名" :label-width="formLabelWidth">
          <el-input v-model="tableForm.name" autocomplete="off"/>
        </el-form-item>
        <el-form-item label="电话" :label-width="formLabelWidth">
          <el-input v-model="tableForm.phone" autocomplete="off"/>
        </el-form-item>
        <el-form-item label="邮箱" :label-width="formLabelWidth">
          <el-input v-model="tableForm.email" autocomplete="off"/>
        </el-form-item>
        <el-form-item label="地址" :label-width="formLabelWidth">
          <el-input v-model="tableForm.address" autocomplete="off"/>
        </el-form-item>
        <el-form-item label="状态" :label-width="formLabelWidth">
          <el-input v-model="tableForm.status" autocomplete="off"/>
        </el-form-item>
      </el-form>
      <template #footer>
      <span class="dialog-footer">
        <el-button type="primary" @click="dialogFormVisible = false">确认</el-button>
      </span>
      </template>
    </el-dialog>
  </div>

</template>


<script setup>
import {Search} from '@element-plus/icons-vue'
// 数据
let queryInput = $ref("")
let multipleSelection = $ref({})
let dialogFormVisible = $ref(false)
let tableForm = $ref({
  name: 'Tom',
  phone: 'California',
  email: 'Los Angeles',
  address: 'No. 189, Grove St, Los Angeles',
  status: 'CA 90036',
})
let tableData = $ref([
  {
    name: 'Tom',
    phone: 'California',
    email: 'Los Angeles',
    address: 'No. 189, Grove St, Los Angeles',
    status: 'CA 90036',
  },
  {
    name: 'Tom',
    phone: 'California',
    email: 'Los Angeles',
    address: 'No. 189, Grove St, Los Angeles',
    status: 'CA 90036',
  },
  {
    name: 'Tom',
    phone: 'California',
    email: 'Los Angeles',
    address: 'No. 189, Grove St, Los Angeles',
    status: 'CA 90036',
  },
  {
    name: 'Tom',
    phone: 'California',
    email: 'Los Angeles',
    address: 'No. 189, Grove St, Los Angeles',
    status: 'CA 90036',
  },

])
const formLabelWidth = '140px'

// 方法
const handleSelectionChange = (val) => {
  multipleSelection = val
  console.log(val);
}

const handleClick = () => {
  console.log('click')
}

const editForm = () => {
  dialogFormVisible = true
}

const addForm = () => {
  dialogFormVisible = true

}


</script>


<style scoped>
.table-box {
  width: 800px;
  margin: 200px auto;
}

.table-title {
  text-align: center;
}

.query-box {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

.table-body {
  margin-top: 20px;
}

.query-input {
  width: 200px;
}

</style>
