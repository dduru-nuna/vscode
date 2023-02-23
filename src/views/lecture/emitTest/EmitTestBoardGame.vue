<template>
    <v-container>
        <table-component 
            :table-data="tableData"
            :current-turn-shape="currentTurnShape"
            @updateTurnShape="updateTurnShape"/>
    </v-container>
</template>

<script>

// 오목 게임
// 바둑판, 승자 판정
// 누구 차례인지 어떻게 알지?
// 'O','X' 표시로 순서를 구분하자!
import TableComponent from '@/components/lecture/emitTest/TableComponent.vue';

export default {
    name: "EmitTestBoardGame",
    components: {
        TableComponent
    },
    data () {
        return {
            currentTurnShape: 'O',
            tableData: [
                ['', '', '', ''],
                ['', '', '', ''],
                ['', '', '', ''],
                ['', '', '', ''],
                ['', '', '', ''],
            ]
        }
    },
    methods: {
        updateTurnShape (receivedTurnShape) {
            console.log('Board Game Component received Table Component info: ' + receivedTurnShape)

            this.currentTurnShape = receivedTurnShape;
        }
    }
}

</script>