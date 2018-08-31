<template>
  <div  class="single-selection">
    <ul class="single-selection-list">
        <li 
            :class="{active:checkChooesd(itemd.id)}" 
            v-for="(itemd, index) in caseList" 
            v-bind:key="itemd.name"
            @click="chooesdEvent (index)"
        >{{itemd.name}}</li>
       
    </ul>
  </div>
  
</template>

<script>
export default {
    props:{
        caseList:{
            type:Array,
            default:function() {
                return [
                    {
                        name:"加载中",
                        id:-10
                    }
                ]
            }
        }
    },
    data () {
        return{
            choosedIndex:[0],
            choosedIndexId:['']
        }
    },
    methods:{
        chooesdEvent (index) {
            this.choosedIndex.push(index)
            this.choosedIndexId.push(this.caseList[index].id)
            this.$emit("singlechoosed",this.choosedIndexId)
        },
        checkChooesd (chooesd) {
            if(choosedIndexId.indexOf('Sam') > -1){
                return true
            }else{
                return false
            }
        }
    }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.single-selection{
    display: inline-block;
    vertical-align: middle;
}
.single-selection-list:after{
    content: '';
    display: block;
    clear: both;
}
.single-selection-list li{
    padding: 3px 10px;
    float: left;
    border-radius: 4px;
    line-height: 20px;
    margin-right: 10px;
    border:1px solid #ccc;
    transition: all .5s ease-in-out;
    cursor: default;
    box-shadow:inset 1px 2px 2px #666;
}
.single-selection-list li:last-child{
    margin-right: 0;
}
.single-selection-list li:hover,.single-selection-list .active{
    background-color:#4fc08d;
    color: #fff; 
}
</style>
