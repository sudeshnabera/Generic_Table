<template>
  <div class="hello">
  <button  @click="addRow"> Add Row</button>
    <table>
        <thead>
            <tr>
                <th>SL NO</th>
                <th>Name</th>
                <th>Address</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td></td>
                <td></td>
                <td></td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
import axios from 
export default {
  name: 'GenericTable',
  data() {
    return {
      tableData:[]
    }
  },
  mounted () {
    axios
      .get('https://dummy.restapiexample.com/api/v1/employees')
      .then(response => (this.tableData = response))
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        tr:hover {
            background-color: #f1f1f1;
        }
        th {
            padding-top: 12px;
            padding-bottom: 12px;
            background-color: #4CAF50;
            color: white;
        }
</style>
