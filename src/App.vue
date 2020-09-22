<template>
    <div class="">
        <img class="p-img" src="./assets/pizza.jpg">
        <div class="title">Order Chart</div>
        <div class="box">
            <data-table
                    :columns="columns"
                    :items="items"
                    :show-cb="false"
                    action-column="title"

            >

                <template slot="customerName" slot-scope="data">
                    {{data.row.customerName}}
                </template>
                <template slot="unit" slot-scope="data">
                    {{data.row.unit}}
                </template>

                <template slot="price" slot-scope="data">
                    {{data.row.price}}
                </template>
                <template slot="amount" slot-scope="data">
                    {{ data.row.unit * data.row.price}}
                </template>
                <template slot="status">
                    <button class="btn"
                            :disabled="this.title === 'Ready to serve'"
                            :style="myStyle">
                        {{title}}
                    </button>
                </template>
            </data-table>

        </div>
    </div>
</template>

<script>
    import dataTable from 'shapla-data-table';
    import jQuery from 'jquery'
    export default {
        name: "App",
        components: {
            dataTable,
        },
        data() {
            return {
                myStyle: {
                    backgroundColor: "#f9a73b"
                },
                title: 'View Status',
                title1: 'Order Received',
                title2: 'Preparing',
                title3: 'Ready to serve',
                customerName: '',
                unit: '',
                price: '',
                columns: [
                    {key: 'id', label: 'SN',},
                    {key: 'customerName', label: 'Customer Name'},
                    {key: 'unit', label: ' No. of Items ordered'},
                    {key: 'price', label: 'Price'},
                    {key: 'amount', label: 'Amount(INR)'},
                    {key: 'status', label: 'Status'},
                ],
                actions: [
                    {event_name: 'getStatus'},
                ],
                items: [
                    {
                        id: 1,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 2,
                        customerName: 'Annu',
                        unit: '3',
                        price: '300',
                    }, {
                        id: 3,
                        customerName: 'sivani',
                        unit: '1',
                        price: '300',
                    },
                    {
                        id: 4,
                        customerName: 'jyotsna',
                        unit: '4',
                        price: '300',
                    }, {
                        id: 5,
                        customerName: 'nea',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 6,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    }, {
                        id: 7,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 8,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    }, {
                        id: 9,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 10,
                        customerName: 'simpi',
                        unit: '1',
                        price: '300',
                    }, {
                        id: 11,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 12,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    }, {
                        id: 13,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 14,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    }, {
                        id: 15,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 16,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    }, {
                        id: 17,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },
                    {
                        id: 18,
                        customerName: 'simpi',
                        unit: '2',
                        price: '300',
                    },

                ]
            }
        },

        computed: {
            total() {
                return this.items.reduce(
                    (acc, item) => acc + item.price * item.unit);
            },

        },
        mounted() {
            var fr = this;
            jQuery(document).on("click", ".btn", function () {
                if (jQuery(this).text()=== ' View Status ') {
                    jQuery(this).css("background", "#00d17a");
                    jQuery(this).val(fr.title1);
                    jQuery(this).html(fr.title1);
                    return false;
                }

                 if ( jQuery(this).val() === "Order Received") {
                    jQuery(this).css("background", "#36d0c9fa");
                    jQuery(this).html(fr.title2);
                    jQuery(this).val(fr.title2);
                     return false;
                }

                 if ( jQuery(this).val() === 'Preparing') {
                    jQuery(this).css("background", "#fe6c61");
                    jQuery(this).html(fr.title3);
                    jQuery(this).val(fr.title3);
                     return false;
                }


            });
        },


    }

</script>

<style lang="scss">
    .title {
        text-align: center;
        color: #f9a73b;
        font-size: 32px;
        font-weight: 600;
        margin-top: 90px;
    }

    .box {
        position: absolute;
        left: 10vw;
        top: 150px;
        width: 80vw;
        height: 75vh;
        overflow: hidden;
        overflow-y: scroll;
    }

    .btn {
        font-size: 12px;
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 20px;
        padding-right: 20px;
        width: 120px;
        color: #ffffff;
        border: none !important;
    }

    .p-img {
        width: 75px;
        height: 75px;
        border-radius: 50%;
        position: absolute;
        top: 15px;
        left: 50%;
        transform: translate(-50%);
    }

    .shapla-data-table__header-cell {
        font-weight: 700;
        color: #000;
        font-size: 18px;
    }

    .shapla-data-table__cell, .shapla-data-table__header-cell {
        text-align: center !important;
    }
</style>
