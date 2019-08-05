<template>
    <div style="padding:50px">
        <el-autocomplete
        v-model="value"
        :fetch-suggestions="querySearchAsync"
        placeholder="请输入内容"
        @select="handleSelect"
        ></el-autocomplete>
    </div>
</template>

<script>
export default {
    data(){
        return{
            list:[
                {text:"abc"},
                {text:"bbc"},
                {text:"bbb"},
                {text:"ccb"}
            ],
            value:"",//输入框值
        }
    },


    methods:{
        //value就是输入框的值
        // cb就是回调函数，必须调用，调用时候接受数组，数组必须是一个对象，
        // 对象必须包含value属性
        querySearchAsync(value,cb){
            // 要显示在页面上的数组
            var arr = []
            // console.log(value)
            // 过滤value属性，从list数据判断
            this.list.forEach(v=>{
                // 判断字符串是否包含输入框的值
                if(v.text.indexOf(value)){
                    v.value=v.text;
                    arr.push(v)
                }
            })
            cb(arr)
        },
        handleSelect(item){
            console.log(item)
        }
    }
}
</script>

<style>

</style>
