#### main.js

// 引入导出excel包

import Blob from './vendor/Blob'

import Export2Excel from './vendor/Export2Excel.js'



#### package.json

"file-saver": "^2.0.2",

"xlsx": "^0.14.5"



#### **.vue

//前端导出Excel表格

  export2Excel(){

​    if (true){

​     import('@/vendor/Export2Excel').then(excel => {

​      const tHeader = [ '医生姓名', '咨询人次', '开单人次', '开单金额'];

​      const filterVal = [ 'doctor', 'zxrc', 'kdrc', 'invAmt']; //table表格中对应的属性名

​      const list = this.tableData

​      console.log(list)

​      const data = this.formatJson(filterVal, list)

​      excel.export_json_to_excel({

​       header: tHeader,

​       data,

​       filename: '报表一'

​      })

​     })

​    } 

  },

  formatJson(filterVal, jsonData) {

   return jsonData.map(v => filterVal.map(j => v[j]))

  }





