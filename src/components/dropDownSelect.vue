<template>
  <div  class="drop-down-select">
    <div class="drop-down-select-content" @click="dropDown">
        <div class="celsct-content">{{chooesList[choosedIndex].name}}</div>
        <div class="arrow" :class="{'rota-x':isShow}"></div>
        <transition name="slide-down">
            <ul v-if="isShow" class="select-list">
                <li 
                    v-for="(chooesd, index) in chooesList" 
                    v-bind:key="chooesd.name"
                    @click="chooesdEvent(index)"
                >
                    {{chooesd.name}}
                </li>
            </ul>
        </transition>
    </div>
  </div>
  
</template>

<script>
export default {
    props:{
        chooesList:
        {
            type:Array,
            default: [
                {
                    name:"加载中....",
                    id:-10
                }
            ]
        }
         
    },
    data () {
        return{
            choosedIndex:0,
            isShow:false,
        }
    },
    methods:{
        chooesdEvent (index) {
            this.choosedIndex=index
            this.$emit("singlechoosed",this.chooesList[index].id)
        },
        dropDown () {
            this.isShow=!this.isShow
        }
    }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.drop-down-select{
    display: inline-block;
    vertical-align: middle;
}
.drop-down-select-content{
    height: 24px;
    line-height: 24px;
    border:1px solid #ccc;
    padding-left:10px; 
    position: relative;
    background: #fff;
    display: inline-block;
}
.drop-down-select-content:after{
    content: '';
    display: block;
    clear: both;
}
.celsct-content{
    float: left;
}
.arrow{
    float: right;
    margin:6px 10px 0 10px;
    width: 0;
    height: 0;
    border-bottom: 10px solid #999;
    border-left: 5px solid transparent ;
    border-right: 5px solid transparent ;
    transition: all .5s ease-in-out;
}
.select-list{
    width: 100%;
    position: absolute;
    left: -1px;
    top: 24px;
    border:1px solid #ccc;
    z-index: 0;
}
.select-list li{
    display: inline-block;
    padding-left:10px;
    background: #fff; 
    height: 24px;
    line-height: 24px;
    width:100%;
    box-sizing: border-box;
    transition: all .5s ease-in-out;
    cursor: default;
}
.select-list li:hover{
    background: #ccc;
    color: #fff;
}
.slide-down-enter,.slide-down-leave-to{
    opacity: 0;
}
.slide-down-leave-active,.slide-down-enter-active{
    transition: all .5s ease-in-out;
}
.rota-x{
    transform: rotateZ(180deg);
}
</style>
