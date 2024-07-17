<template>
  <div class="hello">
    <button @click="addRow"> Add Row</button>
    <table>
      <thead>
        <tr>
          <th>SL NO</th>
          <th>Name</th>
          <th>Email</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="tbData in tableData" :key="tbData.id" :id="'row-' + tbData.id">
          <td>{{ tbData.id }}</td>
          <td>{{ tbData.name }}</td>
          <td>{{ tbData.email }}</td>
          <td><button @click="deleteRow(tbData.id)">Delete</button></td>
        </tr>
        <tr v-if="isAddingNewRow">
          <td><input v-model="newRow.id" placeholder="ID"></td>
          <td><input v-model="newRow.name" placeholder="Name"></td>
          <td><input v-model="newRow.email" placeholder="Email"></td>
          <td><button @click="submitNewRow">Submit</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
// import axios from 'axios';
export default {
  name: 'GenericTable',
  data() {
    return {
      tableData:  [
        { id: 1, name: 'John Doe', email: 'john@example.com' },
        { id: 2, name: 'Jane Doe', email: 'jane@example.com' },
      ],
      isAddingNewRow: false,
      newRow: {
        id: '',
        name: '',
        email: ''
      }
  }
},
  methods: {
    addRow() {
      console.log("add row called");
      this.isAddingNewRow = true;
     
    },
    submitNewRow() {
      if (this.newRow.id && this.newRow.name && this.newRow.email) {
        this.tableData.push({ ...this.newRow });
        this.newRow = { id: '', name: '', email: '' };
        this.isAddingNewRow = false;
      } else {
        console.log("Please fill in all fields");
      }
    },
    deleteRow(rowId){
      this.tableData = this.tableData.filter(row => row.id !== rowId);
        // const rowElement = document.getElementById(`row-${rowId}`);
        // if (rowElement) {
        //   rowElement.remove();
        // }
    }
  }
  };

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
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
