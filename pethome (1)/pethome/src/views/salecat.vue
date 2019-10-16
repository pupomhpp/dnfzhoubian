<template>
    <div>
        <my-header></my-header>
        <main class="container text-center">
            <div class="left">
            <!-- 卖 -->
            <!-- title VARCHAR(128), #主标题 -->
            <div>
                <b>宠物名</b><span>(最好还是填一下)</span> <br> 
                <input>  
            </div>
            <!-- subtitle VARCHAR(128),  #副标题 -->
            <div>
                <b>宠物概述</b><span>(最好还是填一下)</span> <br> 
                <input>  
            </div>
            <!-- family_id INT,      #宠物品种家族编号 -->
            <div>
                品种：
                    <select>
                        <option value="">波斯猫</option>
                        <option value="">布偶猫</option>
                        <option value="">加拿大无毛猫</option>
                        <option value="">美国短毛猫</option>
                        <option value="">挪威深林猫</option>
                        <option value="">暹罗猫</option>
                        <option value="">英国短毛猫</option>    
                    </select>
                     
                <!-- <input placeholder="请输入您的宠物名">   -->
                <!-- 复选框 
                (0,'波斯猫'),
                (1,'布偶猫'),
                (2,'加拿大无毛猫'),
                (3,'美国短毛猫'),
                (4,'挪威森林猫'),
                (5,'暹罗猫'),
                (6,'英国短毛猫'),
                (7,'苏格兰折耳猫'),
                (8,'孟买猫'),
                (9,'加菲猫'),
                (10,'孟加拉豹猫');-->
            </div>
            <!-- price DECIMAL(10,2),#价格 -->
            <div>
                <b>预期价格</b><span>(最好还是填一下)</span> <br> 
                <input>  
            </div>
            <!-- aname VARCHAR(32),#宠物昵称 -->
            <div>
                <b>宠物昵称</b><span>(最好还是填一下)</span> <br> 
                <input> 
            </div>
            <!-- age INT,    #宠物年龄 -->
            <div>
                <b>宠物年龄</b><span>(最好还是填一下)</span> <br> 
                <input> 
            </div>
            <!-- details VARCHAR(256),#宠物详情 -->
            <div>
                <b>宠物详情</b><span>(最好还是填一下)</span> <br> 
                <input> 
            </div>
            <!-- oldmaster VARCHAR(32),#宠物原主 -->
            <div>
               <b>联系人</b><span>(必填)</span> <br> 
                <input> 
            </div>
            <!-- phone   CHAR(11),    #电话 -->
            <div>
                <b>宠物名</b><span>(最好还是填一下)</span> <br> 
                <input>   
            </div>
            <!-- says VARCHAR(256),#原主人寄语 -->
            <div>
                <b>联系电话</b><span>(必填)</span> <br> 
                <input> 
            </div>
            <div>
                <b>寄语</b><span>(选填)</span> <br> 
                <input> 
            </div>
            <!-- adress     VARCHAR(128),#地址 -->
            <div>
                地址：
                    <select name="provs" @change="sel">
		                <option>—请选择—</option><!--0-->
		                <option>北京市</option><!--1-->
		                <option>天津市</option>
		                <option>河北省</option>
                        <option>上海市</option>
                        <option>深圳市</option>
                        <option>河南省</option>
	                </select>
                    <select name="cities" v-show="show">
	                </select>
                     
                <!-- 复选框 省市县 -->
            </div>
            <div>
                <input type="text" placeholder="请输入详细地址">
            </div>
            <!-- saletime DATE,#寄售时间 获取当前时间-->
            <!-- is_onsale BOOLEAN,#是否可以免费认领 -->
            <div>
                喵赠有缘：<label><input type="radio" value="1" name="sex">是</label><label><input class="sexwoman" type="radio" value="0" name="sex" checked>否</label> 
                <!-- 单选框 是 否 -->
            </div>
            <!-- lg VARCHAR(128),#大图 -->
            <div>
                上传图片： 
                <!-- 上传文件 -->
            </div>
            <mt-button>提交</mt-button>
            <!-- 买 -->
            </div>
        </main>
        <my-footer></my-footer>
    </div>
</template>
<script>
export default {
    data(){
        return {
           cities:[
        [{"name":'东城区',"value":101},
       {"name":'西城区',"value":102},
       {"name":'海淀区',"value":103},
       {"name":'朝阳区',"value":104}],
      [{"name":'河东区',"value":201},
       {"name":'河西区',"value":202},
       {"name":'南开区',"value":303}],
      [{"name":'石家庄市',"value":301},
       {"name":'廊坊市',"value":302},
       {"name":'保定市',"value":303},
       {"name":'唐山市',"value":304},
       {"name":'秦皇岛市',"value":304}],
       [{
           "name":'浦东区',"value":401
       },
        {"name":'徐汇区',"value":402},
        {"name":'嘉定区',"value":402},
        {"name":'宝山区',"value":402},
       ],
       [{
           "name":'宝安区',"value":401
       },
        {"name":'盐田区',"value":402},
        {"name":'元朝区',"value":402},
        {"name":'北区',"value":402},
       ],
       [{
           "name":'郑州市',"value":401
       },
        {"name":'洛阳',"value":402},
        {"name":'开封',"value":402},
        {"name":'许昌',"value":402},
       ],
       ],
       show:false
        }
    },
    methods:{
        sel(){
            var selprevo=document.getElementsByName("provs")[0];
            var selcite=document.getElementsByName("cities")[0];
            var selid=selprevo.selectedIndex;
            if(selid==0){
                this.show=false
                return;
            }
            var cts=this.cities[selid-1];
            var frag=document.createDocumentFragment();
            frag.appendChild(new Option("-请选择-"))
            for(var c of cts){
                frag.appendChild(new Option(c.name,c.value))
            }
            selcite.innerHTML="";
            selcite.appendChild(frag);
            this.show=true;
        }
    }
}
</script>
<style  scoped>
    select{
        line-height: 1;
        padding-bottom: 5px;
    }
    .left{
        text-align: left;
        margin-left:400px;
    }
    b{
        font-size:15px;
        font-family: Arial, Helvetica, sans-serif
    }
    span{
        font-size:12px;
        color:#666;
    }
    div{
        margin:5px 0px;
    }
</style>