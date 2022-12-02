
<script>



    // const test = new Grid(this.props.columns({name:'title'}));

import Grid from "gridjs-svelte"

    // let data;
    // new Grid({target:})
    //
    //
    // const data2 = [
    //    { name: "John", email: "john@example.com" },
    //    { name: "Mark", email: "mark@gmail.com" },
    //  ]

    const columns = [
        {
            name: '정산일'
        },
        {
            name: '기성금액', columns:[
                {name: '원도급기성', sort:false},
                {name: '당사수령금액', sort:false}
            ]
        },


                {name: '자재비', columns:[
                        {name: '본사자재'},
                        {name: '원장'},
                        {name: '세금계산서'},
                        {name: '카드,영수증'},
                        {name: '소계'},
                    ]},
                {name: '노무비', columns:[
                        {name: '상용(사무직)'},
                        {name: '상용(기술직)'},
                        {name: '일용'},
                        {name: '소계'},
                    ]},
                {name: '경비', columns:[
                        {name: '세금계산서'},
                        {name: '안전관리비'},
                        {name: '카드,영수증'},
                        {name: '소계'},
                    ]},


        {
            name: '합계'
        },
        {
            name: '미지급금액'
        },


                {name: '00건설(공동도급사1)', columns: [
                        {name: '노무비'},
                        {name: '세금계산서'},
                        {name: '소계'},

                    ]
                },
                {name: '00건설(공동도급사2)', columns: [
                        {name: '노무비'},
                        {name: '세금계산서'},
                        {name: '소계'},

                    ]
                },
                {name: '00건설(공동도급사3)', columns: [
                        {name: '노무비'},
                        {name: '세금계산서'},
                        {name: '소계'},

                    ]
                },
                {name: '00건설(공동도급사4)', columns: [
                        {name: '노무비'},
                        {name: '세금계산서'},
                        {name: '소계'},

                    ]
                },


        {
            name: '합계'
        },
        {
            name: '총합계'
        },
        {
            name: '비고'
        }






    ]

    const className= {
        container: "table-wrapper"
    }
    const style =
        {
            table: {
                    'font-size' : '12px',
                    'text-align' : 'center',
                    'white-space' : 'nowrap'
                },
            td:{
                'padding' : '8px 7px'

                    // 'font-size' : '12px'
            },

            header:{
                'border' : '3px solid #ccc',

            }

        }

        const fixedHeader = {
            fixedHeader : true
        }


    const data = [
        ['2022년'+ ' 10'+'월', '10,000,000', '1,000,000','9,000,000','','','10,000,000','5,200','10,005,200','600','300','20','920','10,006,120','','100','200','300','100','200','300','100','200','300','100','200','300','100','200','1,200','10,007,320','1,000,000','5,000'],
        ['1', '12'],
        ['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11'],['2', '11']]

    const dataRowColors = [
        "#0B6121" ,"#0A2A0A"]
    // const width = {width:'500'}

    // const resizable ={resizable: true}

</script>

<Grid {data} {style} {columns} {fixedHeader} {dataRowColors} {className}/>

