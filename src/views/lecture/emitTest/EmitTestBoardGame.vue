<template>
    <v-container>
        <div>{{ currentTurnShape }} 님의 턴입니다.</div>
        <table-component 
            :table-data="tableData"
            :current-turn-shape="currentTurnShape"
            @updateTurnShape="updateTurnShape"
            @updateWinner="updateWinner"
            @updateTableData="updateTableData"/>
        <div v-if="winner">{{ winner }} 님의 승리!</div>
        <!--winner 가 있으면 보여짐-->
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
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
            ],
            winner: '',
        }
    },
    methods: {
        updateTurnShape (receivedTurnShape) {
            console.log('Board Game Component received Table Component info: ' + receivedTurnShape)
            //하위에서 전달받은 턴 값을 currentTurnShape로 저장
            this.currentTurnShape = receivedTurnShape
        },
        updateWinner (receivedWinner) {
            console.log("Board Game Component: winner received")
            this.winner = receivedWinner
        },
        updateTableData () {
            this.tableData =  [
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
            ]
        }
    }
}

</script>