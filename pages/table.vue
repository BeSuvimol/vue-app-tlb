<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template slot="headerCell" slot-scope="props">
        <v-tooltip bottom>
          <span slot="activator">
            {{ props.header.text }}
          </span>
          <span>
            {{ props.header.text }}
          </span>
        </v-tooltip>
      </template>
      <template slot="items" slot-scope="props">
        <td>{{ props.item.s_code }}</td>
        <td class="text-xs-left">{{ props.item.s_name }}</td>
        <td class="text-xs-left">{{ props.item.s_class }}</td>
        <td class="text-xs-left">{{ props.item.s_group }}</td>
      </template>
    </v-data-table>
 
  </div>
</template>
<script>
export default {
  data () {
    return {
      headers: [
        {
          text: 'น้ำผลไม้',
          align: 'left',
          sortable: false,
          value: 'name',
        },
        { text: 'เย็น', value: 'เย็น' },
        { text: 'ปั่น', value: 'ปั่น' },
        { text: 'เพิ่มไข่มุก', value: 'เพิ่มไข่มุก' },
        
      ],
      desserts: [],
    }
  },
async created() {
  // เรียกใช้งาน
    this.getstudent()
  }, 
methods: {
    async getstudent() {
      let res = await this.$http.get('http://127.0.0.1/php-api/list-student.php')
      this.desserts = res.data.student 
      // ตัวแปล
    },
}
}
</script>