<template>
  <tr>
    <!-- arr[rowIndex][index] 
        rowData -> arr[0] ~ arr[4]
        rowData[0] -> arr[0][0] ~ arr[4][4] -> cellData
                   ...
        rowData[4] -> arr[4][0] ~ arr[4][4] -> cellData
    --> 
    <td-component
        v-for="(cellData, index) in rowData" :key="index"
        :cell-data="cellData"
        :cell-index="index"
        :row-index="rowIndex"
        :table-data="tableData"
        :current-turn-shape="currentTurnShape"
        @updateTurnShape="updateTurnShape"/>
        <!-- @updateTurnShape는 v-on:updateTurnShape와 동의어
            updateTurnShape이라는 이벤트가 발생하면
            updateTurnShape 메서드를 동작시키라는 의미
            만약 @updateTurnShpae="testFunction" 이라면
            updateTurnShape 이벤트 발생시 testFunction 메서드 동작-->
  </tr>
</template>

<script>
import TdComponent from '@/components/lecture/emitTest/TdComponent.vue';

export default {
    name: "TrComponent",
    components: {
        TdComponent
    },
    props: {
        rowData: Array,
        rowIndex: Number,
        tableData: Array,
        currentTurnShape: String,
    },
    methods: {
        updateTurnShape (receivedTurnShape) {
            console.log('Tr Component received Td Component info: ' + receivedTurnShape)

            this.turnShape = receivedTurnShape;
            this.$emit('updateTurnShape', this.turnShape)
        }
    }
}
</script>

<style>

</style>