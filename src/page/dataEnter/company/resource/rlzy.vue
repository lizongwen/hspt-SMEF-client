<template>
  <div>
    <el-tabs v-model="activeName">
      <el-tab-pane label="经营管理团队分析" name="first">
        <div>
          <el-card class="box-card" shadow='nevner'>
            <div slot="header" class="clearfix">
              <div class="card-right-wrap">
                <el-button @click="saveForm" type="primary" size="medium" :loading="loadingStatus">保存</el-button>
              </div>
              <div class="card-title">团队成员</div>
            </div>
            <!-- 循环表单 -->
            <div v-for="(formItem,index) in formArry" :key="index" class="form-item">
              <el-form class="form clearfix" size="small" :label-position="labelPosition" label-width="130px"
                       :model="formItem" ref="form">
                <el-row>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="职务:">
                      <el-input v-model="formItem.zw"></el-input>
                    </el-form-item>
                  </el-col>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="是否参与日常运营:">
                      <el-select v-model="formItem.sfcyrcyy" placeholder="请选择" style="width:100%">
                        <el-option label="参与" value="1"></el-option>
                        <el-option label="不参与" value="0"></el-option>
                      </el-select>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="姓名:">
                      <el-input v-model="formItem.xm"></el-input>
                    </el-form-item>
                  </el-col>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="性别:">
                      <el-select v-model="formItem.xb" placeholder="请选择" style="width:100%">
                        <el-option label="男" value="1"></el-option>
                        <el-option label="女" value="0"></el-option>
                      </el-select>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="文化程度:">
                      <el-select v-model="formItem.whcd" placeholder="请选择" style="width:100%">
                        <el-option label="小学" value="1"></el-option>
                        <el-option label="初中" value="2"></el-option>
                        <el-option label="高中" value="3"></el-option>
                        <el-option label="大专" value="4"></el-option>
                        <el-option label="本科" value="5"></el-option>
                        <el-option label="研究生" value="6"></el-option>
                        <el-option label="博士生" value="7"></el-option>
                      </el-select>
                    </el-form-item>
                  </el-col>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="出生年月:">
                      <el-date-picker v-model="formItem.csny" type="date" placeholder="选择日期"
                                      style="width:100%"></el-date-picker>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="相关工作年限:">
                      <el-input v-model="formItem.xggznl"></el-input>
                    </el-form-item>
                  </el-col>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="婚姻状况:">
                      <el-select v-model="formItem.hyzt" placeholder="请选择" style="width:100%">
                        <el-option label="未婚" value="0"></el-option>
                        <el-option label="已婚" value="1"></el-option>
                      </el-select>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row>
                  <el-col :offset="1" :span="10">
                    <el-form-item label="任职性质:">
                      <el-input v-model="formItem.rzxz"></el-input>
                    </el-form-item>
                  </el-col>
                </el-row>
                <el-row>
                  <el-col :offset="1" :span="21">
                    <el-form-item label="工作履历:">
                      <el-input type="textarea" :rows="5" v-model="formItem.gzll"></el-input>
                    </el-form-item>
                  </el-col>
                </el-row>
              </el-form>
            </div>
            <v-formAddBtn v-on:addForm="addForm"></v-formAddBtn>
          </el-card>
        </div>
        <div>
          <el-card class="box-card" shadow='nevner'>
            <div slot="header" class="clearfix">
              <div class="card-right-wrap">
                <el-button class="save" type="primary" size="medium" @click="saveTdXj">保存</el-button>
              </div>
              <div class="card-title">小结</div>
            </div>
            <div class="text-editor">
              <quill-editor :value="tdxj" :maxSize="10240" v-on:changeInput="changTdxj"></quill-editor>
            </div>
          </el-card>
        </div>
      </el-tab-pane>
      <el-tab-pane label="员工分析" name="second">
        <div>
          <el-card class="box-card" shadow='nevner'>
            <div slot="header" class="clearfix">
              <div class="card-right-wrap">
                <el-button class="save" type="primary" size="medium" @click="saveYgfx" :loading="loadingStatus">保存</el-button>
              </div>
              <div class="card-title">公司员工分析</div>
            </div>
            <!-- 表格容器 -->
            <div>
              <el-table :data="formatterTableData" v-loading.body="listLoading" border fit highlight-current-row
                        show-summary :summary-method="getSummaries" style="width: 100%">
                <el-table-column min-width="100px" label="部门" prop="department">
                  <template slot-scope="scope">
                    <template v-if="scope.row.edit">
                      <el-form :model="scope.row" :rules="rules_ygfx" :id="'department'+scope.$index"
                               :ref="'form_department_'+scope.$index" :show-message="false">
                        <el-form-item prop="department" class="td-form-item">
                          <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[1]" size="small" v-model="scope.row.bm"></el-input>
                        </el-form-item>
                      </el-form>
                    </template>
                    <span v-else>{{scope.row.bm}}</span>
                  </template>
                </el-table-column>
                <el-table-column min-width="100px" label="学历结构">
                  <el-table-column min-width="100px" label="初中及以下" prop="czjyx">
                    <template slot-scope="scope">
                      <template v-if="scope.row.edit">
                        <el-form :model="scope.row" :rules="rules_ygfx" :id="'junior'+scope.$index"
                                 :ref="'form_junior_'+scope.$index" :show-message="false">
                          <el-form-item prop="junior" class="td-form-item">
                            <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[2]" size="small" v-model="scope.row.czjyx"></el-input>
                          </el-form-item>
                        </el-form>
                      </template>
                      <span v-else>{{ scope.row.czjyx}}</span>
                    </template>
                  </el-table-column>
                  <el-table-column min-width="100px" label="高中" prop="gz">
                    <template slot-scope="scope">
                      <template v-if="scope.row.edit">
                        <el-form :model="scope.row" :rules="rules_ygfx" :id="'middle'+scope.$index"
                                 :ref="'form_middle_'+scope.$index" :show-message="false">
                          <el-form-item prop="middle" class="td-form-item">
                            <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[3]" size="small" v-model="scope.row.gz"></el-input>
                          </el-form-item>
                        </el-form>
                      </template>
                      <span v-else>{{ scope.row.gz}}</span>
                    </template>
                  </el-table-column>
                  <el-table-column min-width="100px" label="大学及以上" prop="dxjys">
                    <template slot-scope="scope">
                      <template v-if="scope.row.edit">
                        <el-form :model="scope.row" :rules="rules_ygfx" :id="'senior'+scope.$index"
                                 :ref="'form_senior_'+scope.$index" :show-message="false">
                          <el-form-item prop="senior" class="td-form-item">
                            <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[4]" size="small" v-model="scope.row.dxjys"></el-input>
                          </el-form-item>
                        </el-form>
                      </template>
                      <span v-else>{{ scope.row.dxjys}}</span>
                    </template>
                  </el-table-column>
                </el-table-column>
                <el-table-column min-width="100px" label="小计" prop="hj">
                  <template slot-scope="scope">
                    <template v-if="scope.row.edit">
                      <el-form :model="scope.row" :rules="rules_ygfx" :id="'subtotal'+scope.$index"
                               :ref="'form_subtotal_'+scope.$index" :show-message="false">
                        <el-form-item prop="subtotal" class="td-form-item">
                          <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[5]" size="small" v-model="scope.row.hj"></el-input>
                        </el-form-item>
                      </el-form>
                    </template>
                    <span v-else>{{ scope.row.hj}}</span>
                  </template>
                </el-table-column>
                <el-table-column min-width="100px" label="在职年限" prop="workYear">
                  <template slot-scope="scope">
                    <template v-if="scope.row.edit">
                      <el-form :model="scope.row" :rules="rules_ygfx" :id="'workYear'+scope.$index"
                               :ref="'form_workYear_'+scope.$index" :show-message="false">
                        <el-form-item prop="workYear" class="td-form-item">
                          <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[6]" size="small" v-model="scope.row.pjzznx"></el-input>
                        </el-form-item>
                      </el-form>
                    </template>
                    <span v-else>{{ scope.row.pjzznx}}</span>
                  </template>
                </el-table-column>
                <el-table-column min-width="100px" label="平均年龄" prop="averagAge">
                  <template slot-scope="scope">
                    <template v-if="scope.row.edit">
                      <el-form :model="scope.row" :rules="rules_ygfx" :id="'averagAge'+scope.$index"
                               :ref="'form_averagAge_'+scope.$index" :show-message="false">
                        <el-form-item prop="averagAge" class="td-form-item">
                          <el-input class="edit-input cellItem el-form-item" :class="Object.keys(formatterTableData_columns)[7]" size="small" v-model="scope.row.pjnl"></el-input>
                        </el-form-item>
                      </el-form>
                    </template>
                    <span v-else>{{ scope.row.pjnl}}</span>
                  </template>
                </el-table-column>
                <el-table-column align="center" label="操作" width="240">
                  <template slot-scope="scope">
                    <v-tableOperation :scope="scope" :tableData="formatterTableData" v-on:verify="verify"
                                      v-on:acceptDelRow='acceptDelRow'></v-tableOperation>
                  </template>
                </el-table-column>
              </el-table>
              <v-tabelAddBtn :tableData="formatterTableData"
                             :tableData_columns="formatterTableData_columns"></v-tabelAddBtn>
            </div>
          </el-card>
        </div>
        <div>
          <el-card class="box-card" shadow='nevner'>
            <div slot="header" class="clearfix">
              <div class="card-right-wrap">
                <el-button class="save" type="primary" size="medium" @click="saveYgXj">保存</el-button>
              </div>
              <div class="card-title">小结</div>
            </div>
            <div class="text-editor">
              <quill-editor :value="ygxj" :maxSize="10240" v-on:changeInput="changYgxj"></quill-editor>
            </div>
          </el-card>
        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
  import tableValidates from "@/utils/validateTable/tableValidates.js";
  import quillEditor from "@/components/form/quillEditor.vue";
  import formAddBtn from "@/components/form/form-add-btn.vue";
  import tabelAddBtn from "@/components/table/table-add-btn.vue";
  import tableOperation from "@/components/table/table-operation.vue";

  export default {
    data() {
      return {
        activeName: "first",
        listLoading: false,
        loadingStatus: false,
        tdxj: "",
        ygxj: "",
        labelPosition: "right",
        formArry: [],
        formArryObj: {
          id: null,
          zw: "职务",
          sfcyrcyy: "是否参与日常运营",
          xm: "姓名",
          xb: "性别",
          whcd: "文化程度",
          csny: "出生年月",
          xggznl: "相关工作年龄",
          hyzt: "婚姻状态",
          rzxz: "任职性质",
          gzll: "工作履历",
        },
        formArry_bf: [],
        formArry_add: [],
        formArry_update: [],
        formArry_del: [],
        ///////////////////////////////////////////////////////

        formatterTableData: [],
        addData: [],
        updateData: [],
        delRowData: [],
        formatterTableData_columns: {
          id: "",
          bm: "", //部门
          czjyx: null, //初中及以下
          gz: null, //高中
          dxjys: null, //大学及以上
          hj: null, //小计
          pjzznx: null, //在职年限
          pjnl: null, //平均年龄
          edit: false
        },
        //规则
        rules_ygfx: {
          bm: [{ required: true, message: "部门是必填项" }],
          czjyx: [{ required: true, message: "初中及以下是必填项" },
            {validator(rule, value, callback) {
                var errors = [];
                if (!/^(0|\+?[1-9][0-9]*)$/.test(value)) {

                  callback('此项必须是整数值....');
                }
                callback(errors);

              }}
          ],
          gz: [{ required: true, message: "高中是必填项" },
            {validator(rule, value, callback) {
                var errors = [];
                if (!/^(0|\+?[1-9][0-9]*)$/.test(value)) {

                  callback('此项必须是整数值....');
                }
                callback(errors);

              }}
          ],
          dxjys: [{ required: true, message: "大学及以上是必填项" },
            {validator(rule, value, callback) {
                var errors = [];
                if (!/^(0|\+?[1-9][0-9]*)$/.test(value)) {

                  callback('此项必须是整数值....');
                }
                callback(errors);

              }}

          ],
          hj: [{ required: true, message: "小计是必填项" },
            {validator(rule, value, callback) {
                var errors = [];
                if (!/^(0|\+?[1-9][0-9]*)$/.test(value)) {

                  callback('此项必须是整数值....');
                }
                callback(errors);

              }}
          ],
          pjzznx: [{ required: true, message: "在职年限是必填项" },
            {validator(rule, value, callback) {
                var errors = [];
                if (!/^[+]{0,1}(\d+)$|^[+]{0,1}(\d+\.\d+)$/.test(value)) {

                  callback('此项必须是数值....');
                }
                callback(errors);

              }}
          ],
          pjnl: [{ required: true, message: "平均年龄是必填项" },
            {validator(rule, value, callback) {
                var errors = [];
                if (!/^[+]{0,1}(\d+)$|^[+]{0,1}(\d+\.\d+)$/.test(value)) {

                  callback('此项必须是数值....');
                }
                callback(errors);

              }}
          ]

        },
      };
    },
    mounted() {
      this.getJygltd(); //经营团队分析
      this.getGltdxj(); //经营团队分析小结
      this.getYgfx(); //员工分析
      this.getYgfxxj(); //员工分析小结
    },
    methods: {
      //--------------------------经营管理团队分析----------------------------------//

      //获取经营管理团队分析
      getJygltd: async function () {
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token")
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/jygltdfx/list",
          params
        );
        this.formArry = res.data.resultData.data.rows;
        this.formArry_bf = JSON.parse(JSON.stringify(this.formArry));
      },
      //增加表单
      addForm() {
        let newData = JSON.parse(JSON.stringify(this.formArryObj));
        for (let key in newData) {
          newData[key] = null;
        }
        this.formArry.push(newData);
      },
      //保存表单
      saveForm: async function () {
        this.loadingStatus = true;
        this.formArry.forEach((item, index) => {
          if (item.id == null) {
            if(item.zw != null &&
              item.sfcyrcyy != null &&
              item.xm != null &&
              item.xb != null &&
              item.whcd != null &&
              item.csny != null &&
              item.xggznl != null &&
              item.hyzt != null &&
              item.rzxz != null &&
              item.gzll != null ){
              this.formArry_add.push(item);
            }
          } else if (item.id != null) {
            this.formArry_bf.forEach((value, key) => {
              if (value.id == item.id && JSON.stringify(item) != JSON.stringify(value)) {
                this.formArry_update.push(item);
              }
            })
          }
        });
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token"),
          addData: JSON.stringify(this.formArry_add),
          updateData: JSON.stringify(this.formArry_update),
          delData: JSON.stringify(this.formArry_del)
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/jygltdfx/save",
          params
        );
        if (res.data.resultCode == "0") {
          this.$message({message: res.data.resultMsg, type: "success"});
          this.getJygltd();
        } else {
          this.$message({message: res.data.resultMsg, type: "warning"});
        }
        this.loadingStatus = false;
        this.formArry_add = [];
        this.formArry_update = [];
        this.formArry_del = [];
      },
      //经营管理团队分析小结
      getGltdxj: async function () {
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token")
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/jytdfxxj/list",
          params
        );
        this.tdxj = res.data.resultData.data.jytdfxxj;
      },

      //保存小结
      saveTdXj: async function () {
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token"),
          jytdfxxj: this.tdxj
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/jytdfxxj/save",
          params
        );
        if (res.data.resultCode == "0") {
          this.$message({message: res.data.resultMsg, type: "success"});
          this.getGltdxj();
        } else {
          this.$message({message: res.data.resultMsg, type: "warning"});
        }
      },
      //改变小结内容
      changTdxj(val) {
        this.tdxj = val;
      },

      //--------------------------员工分析----------------------------------//

      //接受删除的数据
      acceptDelRow(val) {
        this.delRowData.push(val);
      },
      //验证数据
      verify(rowObj, rowIndex) {
        var isValid = tableValidates.validateByRow(
          rowObj,
          rowIndex,
          this.rules_ygfx,
          this
        );
        if (rowObj.id) {
          this.updateData.push(rowObj);
        }
      },

      //获取员工分析
      getYgfx: async function () {
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token")
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/gsygfx/list",
          params
        );
        if (res.data.resultCode == "0") {
          this.formatterTableData = res.data.resultData.data;
        }
      },
      //保员工分析数据
      saveYgfx: async function () {
        this.loadingStatus = true;
        this.formatterTableData.forEach((item, index) => {
          if (item.id == null) {
            if(item.bm != null &&
              item.czjyx != null &&
              item.gz != null &&
              item.dxjys != null &&
              item.hj != null &&
              item.pjzznx != null &&
              item.pjnl != null ){
              this.addData.push(item);
            }
          }
        });
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token"),
          addData: JSON.stringify(this.addData),
          updateData: JSON.stringify(this.updateData),
          delData: JSON.stringify(this.delRowData)
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/gsygfx/save",
          params
        );
        if (res.data.resultCode == "0") {
          this.$message({message: res.data.resultMsg, type: "success"});
          this.getYgfx();
        } else {
          this.$message({message: res.data.resultMsg, type: "warning"});
        }
        this.loadingStatus = false;
        this.delRowData = [];
        this.updateData = [];
        this.addData = [];
      },

      //获取员工分析小结
      getYgfxxj: async function () {
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token")
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/gsygfxxj/list",
          params
        );
        if (res.data.resultCode == "0") {
          this.ygxj = res.data.resultData.data.gsygfxxj;
        }
      },

      //保存小结
      saveYgXj: async function () {
        let params = {
          creditCode: sessionStorage.getItem("creditCode"),
          token: sessionStorage.getItem("token"),
          gsygfxxj: this.ygxj
        };
        const res = await this.$http.post(
          "/hspt-web-api/data_entry/gsyyxx/rlzyfx/gsygfxxj/save",
          params
        );
        if (res.data.resultCode == "0") {
          this.$message({message: res.data.resultMsg, type: "success"});
          this.getYgfxxj();
        } else {
          this.$message({message: res.data.resultMsg, type: "warning"});
        }
      },
      //改变小结内容
      changYgxj(val) {
        this.ygxj = val;
      },
      //------------------------------------------------------------------------
      getSummaries(param) {
        const {columns, data} = param;
        const sums = [];
        columns.forEach((column, index) => {
          if (index === 0) {
            sums[index] = "合计";
            return;
          }
          const values = data.map(item => Number(item[column.property]));
          if (!values.every(value => isNaN(value))) {
            sums[index] = values.reduce((prev, curr) => {
              const value = Number(curr);
              if (!isNaN(value)) {
                return prev + curr;
              } else {
                return prev;
              }
            }, 0);
            //根据列名不同，确定不同的合计单位
            if (column.property == "ratio") {
              sums[index] += "%";
            } else if (
              column.property == "subscribe" ||
              column.property == "paidIn"
            ) {
              sums[index] += " 万元";
            }
          } else {
            sums[index] = "";
          }
        });
        return sums;
      }
    },
    components: {
      "v-formAddBtn": formAddBtn,
      "v-tabelAddBtn": tabelAddBtn,
      "v-tableOperation": tableOperation,
      "quill-editor": quillEditor
    }
  };
</script>

<style lang="scss">
  .form-item {
    border-bottom: 1px solid #ebebeb;
    margin-bottom: 20px;
  }

  .text-editor .ql-editor {
    height: 300px;
  }
</style>

