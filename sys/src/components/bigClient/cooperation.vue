<template>
  <div class="container">
    <el-row class="search">
        <el-col :span="2" style="width: 5.5%;line-height: 30px">
          <el-button type="primary" size="small">新增</el-button>
        </el-col>
        <el-col :span="2" style="width: 5.5%;line-height: 30px">
          <span>负责人</span>
        </el-col>
        <el-col :span="2">
          <el-select size="small" v-model="isMember">
            <el-option value="[1, 2, 3]">

            </el-option>
          </el-select>
        </el-col>
        <el-col :span="2" style="width: 5.5%;line-height: 30px">
          <span>区县</span>
        </el-col>
        <el-col :span="2">
          <el-select size="small" v-model="isMember">
            <el-option value="[1, 2, 3]">

            </el-option>
          </el-select>
        </el-col>
        <el-col :span="2" style="width: 5.5%;line-height: 30px">
          <span>机构名称</span>
        </el-col>
        <el-col :span="2">
          <el-input placeholder="请输入机构名称" size="small"></el-input>
        </el-col>
        <el-col :span="2" style="width: 5.5%;line-height: 30px">
          <span>机构类型</span>
        </el-col>
        <el-col :span="2">
          <el-select size="small" v-model="isMember">
            <el-option value="[1, 2, 3]">

            </el-option>
          </el-select>
        </el-col>
        <el-col :span="2" style="width: 5.5%;line-height: 30px">
          <span>机构规模</span>
        </el-col>
        <el-col :span="2">
          <el-select size="small" v-model="isMember">
            <el-option value="[1, 2, 3]">

            </el-option>
          </el-select>
        </el-col>
        <el-col :span="1" style="width: 4.8%;margin-left: 1%;">
          <el-button size="small" type="warning" class="btns">查询</el-button>
        </el-col>
    </el-row>
    <el-row class="client_table">
        <el-col :span="24">
          <el-table :border="true" :data="clientData" style="width: 100%">
            <el-table-column width="60" align="center" type="index" label="序号">

            </el-table-column>
            <el-table-column align="center" prop="name" label="省份" min-width="60"></el-table-column>
            <el-table-column align="center" prop="phone" label="城市" min-width="60"></el-table-column>
            <el-table-column align="center" prop="sex" label="区县" min-width="60"></el-table-column>
            <el-table-column align="center" prop="takePeople" label="机构名称" min-width="60"></el-table-column>
            <el-table-column align="center" prop="productName" label="机构类型" min-width="60"></el-table-column>
            <el-table-column align="center" prop="time" label="对接人姓名" min-width="60"></el-table-column>
            <el-table-column align="center" prop="moduleState" label="对接人电话" min-width="80"></el-table-column>
            <el-table-column align="center" prop="moduleState" label="合同签署日期" min-width="80"></el-table-column>
            <el-table-column align="center" prop="moduleState" label="合同终止日期" min-width="80"></el-table-column>
            <el-table-column align="center" prop="moduleState" label="负责人" min-width="60"></el-table-column>
            <el-table-column align="center" prop="moduleState" label="合同人数" min-width="60"></el-table-column>
            <el-table-column align="center" prop="operation" label="操作" min-width="200">
              <template slot-scope="scope">
                <el-button type="primary" @click="handleOrder(scope.row)" size="small">下载附件</el-button>
                <el-button type="danger" @click="handleOrder(scope.row)" size="small">删除</el-button>
                <el-button type="warning" @click="handleOrder(scope.row)" size="small">修改</el-button>
              </template>
            </el-table-column>
          </el-table>
        </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
      return {
        clientName: '',
        clientPhone: '',
        isMember: '',
        clientData: [{
          name: '张三',
          sex: '男',
          phone: '1829416233',
          takePeople: '王麻子',
          productName: '拉升期',
          moduleState: '完成',
          time: String(new Date().toLocaleDateString()),
          isMember: '是',
        }],
        clientChoseDate: '',
      }
  }
};
</script>

<style scoped lang="scss">
.container{
  width: 100%;
  .search{
    text-align: center; 
  }
  .another_row{
    text-align: center;
    margin-top: 20px;
    span{
      line-height: 30px;
    }
  }
  .client_table{
    margin-top: 20px;
  }
}
</style>
