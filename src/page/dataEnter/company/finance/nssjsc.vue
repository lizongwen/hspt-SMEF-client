<template>
	<div>
		<el-card class="box-card" shadow='nevner'>
			<div slot="header" class="clearfix">
							<div class="card-right-wrap">
								<el-button type="default" size="medium">模板下载</el-button>
								<el-button type="default" size="medium">数据导入</el-button>
								<el-button  type="primary" size="medium">保存</el-button>
							</div>
						</div>
							<!-- 表格容器 -->
						<div>
							
								<div slot="header" class="clearf">
							<div class="card-title">目标公司缴纳各项税款详细如下（单位：万元）</div>
						</div>
							  <!--el-table :data="tableData" border fit highlight-current-row show-summary :summary-method="getSummaries"    style="width: 100%;text-align: center;">
                                <el-table-column prop="project" :label="tableData_columns.project">
                                      <template slot-scope="scope">
                                      	<span>{{ scope.row.project1}}</span>
										<span>{{ scope.row.project2}}</span>
									</template>
                                </el-table-column>
       
                                <el-table-column prop="year1" :label="tableData_columns.year1">
                                    <template slot-scope="scope">
										<span>{{ scope.row.year1}}</span>
									</template>
                                </el-table-column>
                                <el-table-column prop="year2" :label="tableData_columns.year2">
                                	<template slot-scope="scope">
										<span>{{ scope.row.year2}}</span>
									</template>>
                                </el-table-column>
                                <el-table-column prop="year3" :label="tableData_columns.year3">
                                <template slot-scope="scope">
										<span>{{ scope.row.year3}}</span>
									</template>
                                </el-table-column>
                              </el-table-->
                              
                              
                              <!--<div class="el-table el-table--fit el-table--border el-table--enable-row-hover el-table--enable-row-transition" style="width: 100%; text-align: center;">
								  <div class="hidden-columns">
								    <div>--&gt;--&gt;</div>
								    <div></div>
								    <div></div>
								    <div></div>
								  </div>
								  <div class="el-table__header-wrapper">
								    <table cellspacing="0" cellpadding="0" border="0" class="el-table__header" style="width: 1280px;">
								      <colgroup>
								        <col name="el-table_3_column_9" width="320">
								          <col name="el-table_3_column_10" width="320">
								            <col name="el-table_3_column_11" width="320">
								              <col name="el-table_3_column_12" width="320">
								                <col name="gutter" width="0"></colgroup>
								      <thead class="has-gutter">
								        <tr class="">
								          <th colspan="1" rowspan="1" class="el-table_3_column_9     is-leaf">
								            <div class="cell">项目</div></th>
								          <th colspan="1" rowspan="1" class="el-table_3_column_10     is-leaf">
								            <div class="cell">2015</div></th>
								          <th colspan="1" rowspan="1" class="el-table_3_column_11     is-leaf">
								            <div class="cell">2016</div></th>
								          <th colspan="1" rowspan="1" class="el-table_3_column_12     is-leaf">
								            <div class="cell">2017</div></th>
								          <th class="gutter" style="width: 0px; display: none;"></th>
								        </tr>
								      </thead>
								    </table>
								  </div>
								  <div class="el-table__body-wrapper is-scrolling-none">
								    <table cellspacing="0" cellpadding="0" border="0" class="el-table__body" style="width: 1280px;">
								      <colgroup>
								        <col name="el-table_3_column_9" width="320">
								          <col name="el-table_3_column_10" width="320">
								            <col name="el-table_3_column_11" width="320">
								              <col name="el-table_3_column_12" width="320"></colgroup>
								      <tbody>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								          	
								          	<table width="100%" border="0">
								          		<tr height="100">
								          			<td rowspan="2" height="100%">22</td>
								          			<td height="50%">33</td>
								          		</tr>
								          		
								          		<tr height="50%">
								          			<td>212</td>
								          		</tr>
								          	</table>
								           <div class="cell">增值税</div>
								          <div class="cell">实缴额</div>
								          </td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								          	<div class="cell">增值税</div>
								            <div class="cell">退税额</div>
								          </td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">企业所得税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">城建税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">土地使用税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">房产税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">印花税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">营业税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">教育费附加税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">地方教育费附加</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">个人所得税</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">水利基金</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        <tr class="el-table__row">
								          <td class="el-table_3_column_9  ">
								            <div class="cell">其他税费</div></td>
								          <td class="el-table_3_column_10  ">
								            <div class="cell">
								              <span></span>
								            </div>
								          </td>
								          <td class="el-table_3_column_11  ">
								            <div class="cell"></div>
								          </td>
								          <td class="el-table_3_column_12  ">
								            <div class="cell"></div>
								          </td>
								        </tr>
								        </tbody>
								    </table>
								    
								    </div>
								  <div class="el-table__footer-wrapper">
								    <table cellspacing="0" cellpadding="0" border="0" class="el-table__footer" style="width: 1280px;">
								      <colgroup>
								        <col name="el-table_3_column_9" width="320">
								          <col name="el-table_3_column_10" width="320">
								            <col name="el-table_3_column_11" width="320">
								              <col name="el-table_3_column_12" width="320">
								                <col name="gutter" width="0"></colgroup>
								      <tbody class="has-gutter">
								        <tr>
								          <td colspan="1" rowspan="1" class="el-table_3_column_9 is-leaf">
								            <div class="cell">合计</div></td>
								          <td colspan="1" rowspan="1" class="el-table_3_column_10 is-leaf">
								            <div class="cell"></div>
								          </td>
								          <td colspan="1" rowspan="1" class="el-table_3_column_11 is-leaf">
								            <div class="cell"></div>
								          </td>
								          <td colspan="1" rowspan="1" class="el-table_3_column_12 is-leaf">
								            <div class="cell"></div>
								          </td>
								          <th class="gutter" style="width: 0px; display: none;"></th>
								        </tr>
								      </tbody>
								    </table>
								  </div>
								
								  <div class="el-table__column-resize-proxy" style="display: none;"></div>
								</div>-->
                              
                              <table border="1" cellspacing="0" cellpadding="0" style="text-align: center;">
                              	<tr>
                              		<th colspan="2">项目</th>
                              		<th colspan="3">2015年</th>
                              		<!--<th>2016年</th>
                              		<th>2017年</th>-->
                              	</tr>
                             
                              	<tr>
                              		<td rowspan="2">增值税</td>
                              		<td>实缴额</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td>退税额</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">企业所得税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">城建税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">土地使用税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">房产税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">印花税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">营业税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">教育费附加税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">地方教育附加</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">个人所得税</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">水利基金</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">其他税费</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              	<tr>
                              		<td colspan="2">合计</td>
                              		<td colspan="3"></td>
                              		<!--<td></td>
                              		<td></td>-->
                              	</tr>
                              </table>
                             
                            
						</div>
			
		</el-card>
	</div>
</template>

<script>
</script>

<style lang="scss">
	$width: 100%;
$background: #f4f3f3;
$border-collapse: collapse;
 $text-align: center;
table {
  width: $width;
  background: $background;
  border-collapse: $border-collapse;
  text-align: $text-align;
}
/*table tr {
  border-bottom: 1px solid #d8d8d8;
}*/
$width: 50%;
$height: 40px;

$padding-left: 20px;
table tr th {
  width: $width;
  height: $height;

  padding-left: $padding-left;
}
 $height: 40px;

 $padding-left: 20px;
 $background: white;
table tr td {
  height: $height;

  padding-left: $padding-left;
  background: $background;
}
</style>