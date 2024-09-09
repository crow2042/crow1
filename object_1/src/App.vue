<script setup>
  import { reactive,ref } from 'vue';

  
  const startDate = ref('');
  const endDate = ref(new Date().toISOString().slice(0, 10)); // 默认当前日期

  const setDateRange = (months) => {
    const today = new Date();
    endDate.value = today.toISOString().slice(0, 10);

    const pastDate = new Date();
    pastDate.setMonth(today.getMonth() - months);

    startDate.value = pastDate.toISOString().slice(0, 10);
  };


    const switch1 = ref(true);
    const switch2 = ref(true);
    const isChecked1 = ref(false);
    const isChecked2 = ref(false);
    const isChecked3 = ref(true);
    const isChecked4 = ref(false);
    const isChecked5 = ref(true);
    const isChecked6 = ref(true);
    const display1 = ref(true);


    const entrust_vlaue = reactive({
      show:false,
      value:1000000,
    });

    const entrust_gu = reactive({
      show:true,
      value:100,
    });

    const pingheng_entrust_vlaue = reactive({
      show:false,
      value:100,
    });

    const pinghengentrust_gu = reactive({
      show:true,
      value:1000000,
    });



    const handleChange = () => {
      // 确保 isChecked2 始终为 false
      isChecked2.value = false;
      isChecked1.value = !isChecked1.value;
      entrust_gu.show = isChecked1.value;
      entrust_vlaue.show = !isChecked1.value;
      pinghengentrust_gu.show = isChecked1.value;
      pingheng_entrust_vlaue.show = !isChecked1.value;

      // ... 其他更新逻辑
    };

    const handleChange0 = () => {
      // 确保 isChecked1 始终为 false
      isChecked1.value = false;
      isChecked2.value = !isChecked2.value;
      entrust_gu.show = !isChecked2.value;
      entrust_vlaue.show = isChecked2.value;
      pinghengentrust_gu.show = !isChecked2.value;
      pingheng_entrust_vlaue.show = isChecked2.value;

      // ... 其他更新逻辑
    };



    const handleChange1 = (checkbox) => {
      if (checkbox === 'isChecked3') {
        isChecked4.value = false; // 取消勾选非对称网络
        display1.value = true;
      } else {
        isChecked3.value = false; // 取消勾选对称网络
        display1.value = false;
      }
    };


    const details = reactive({
        list: [{
            id: 1,
            name: "xx",
            price: "--",
            price_limit: "--",
            fluctuation:"--"
        }]
    })

    const tips = () =>{
        window.alert('历史波动率用来判断该交易品种是否适合网 格交易，波动率越大越适合做网格交易。')
    }

    const zhangdie = reactive({
      show:true,
      huiluomaichu_show:true,
      guaidianmairu_show:true
    })

    const show_change = () =>{
      zhangdie.show=!zhangdie.show
    }

    const die_value_cent = reactive({
      first_value:null,
      second_value:null,
      first_cent:null,
      second_cent:null
    })

    const zhangdie_value_cent = reactive({
      first_value:null,
      second_value:null,
      first_cent:null,
      second_cent:null
    })

    const value_add = () =>{
      if(zhangdie_value_cent.first_value === null){
        zhangdie_value_cent.first_value=0.01;
      }else{
      zhangdie_value_cent.first_value=(parseFloat(zhangdie_value_cent.first_value) + 0.01).toFixed(2);
      }
    }

    const value_subtract = () => {
      if (zhangdie_value_cent.first_value !== null && parseFloat(zhangdie_value_cent.first_value) > 0.01) {
        zhangdie_value_cent.first_value = (parseFloat(zhangdie_value_cent.first_value) - 0.01).toFixed(2);
      }
    };

    const cent_add = () =>{
      if(zhangdie_value_cent.first_cent === null){
        zhangdie_value_cent.first_cent=0.50;
      }else{
      zhangdie_value_cent.first_cent=(parseFloat(zhangdie_value_cent.first_cent) + 0.01).toFixed(2);
      }
    }

    const cent_subtract = () => {
      if (zhangdie_value_cent.first_cent !== null && parseFloat(zhangdie_value_cent.first_cent) > 0.50) {
        zhangdie_value_cent.first_cent = (parseFloat(zhangdie_value_cent.first_cent) - 0.01).toFixed(2);
      }
    }

    const second_cent_subtract = () =>{
      if(zhangdie_value_cent.second_cent === null){
        zhangdie_value_cent.second_cent=-0.01;
      }else{
      zhangdie_value_cent.second_cent=(parseFloat(zhangdie_value_cent.second_cent) - 0.01).toFixed(2);
      }
    }

    const second_cent_add = () => {
      if (zhangdie_value_cent.second_cent !== null && parseFloat(zhangdie_value_cent.second_cent) < -0.01) {
        zhangdie_value_cent.second_cent = (parseFloat(zhangdie_value_cent.second_cent) + 0.01).toFixed(2);
      }
    }

    const second_value_add = () =>{
      if(zhangdie_value_cent.second_value === null){
        zhangdie_value_cent.second_value=-0.01;
      }else{
      zhangdie_value_cent.second_value=(parseFloat(zhangdie_value_cent.second_value) - 0.01).toFixed(2);
      }
    }

    const second_value_subtract = () => {
      if (zhangdie_value_cent.second_value !== null && parseFloat(zhangdie_value_cent.second_value) < -0.00) {
        zhangdie_value_cent.second_value = (parseFloat(zhangdie_value_cent.second_value) + 0.01).toFixed(2);
      }
    };

    const die_cent_add = () =>{
      if(die_value_cent.first_cent === null){
        die_value_cent.first_cent=-0.50;
      }else{
      die_value_cent.first_cent=(parseFloat(die_value_cent.first_cent) - 0.01).toFixed(2);
      }
    }

    const die_cent_subtract = () => {
      if (die_value_cent.first_cent !== null && parseFloat(die_value_cent.first_cent) < -0.50) {
        die_value_cent.first_cent = (parseFloat(die_value_cent.first_cent) + 0.01).toFixed(2);
      }
    }

    const die_value_add = () =>{
      if(die_value_cent.first_value === null){
        die_value_cent.first_value=-0.01;
      }else{
      die_value_cent.first_value=(parseFloat(die_value_cent.first_value) - 0.01).toFixed(2);
      }
    }

    const die_value_subtract = () => {
      if (die_value_cent.first_value !== null && parseFloat(die_value_cent.first_value) < -0.00) {
        die_value_cent.first_value = (parseFloat(die_value_cent.first_value) + 0.01).toFixed(2);
      }
    }

    const die_second_value_add = () =>{
      if(die_value_cent.second_value === null){
        die_value_cent.second_value=0.0;
      }else{
      die_value_cent.second_value=(parseFloat(die_value_cent.second_value) + 0.01).toFixed(2);
      }
    }

    const die_second_value_subtract = () => {
      if (die_value_cent.second_value !== null && parseFloat(die_value_cent.second_value) > 0.00) {
        die_value_cent.second_value = (parseFloat(die_value_cent.second_value) - 0.01).toFixed(2);
      }
    }

    const die_second_cent_add = () =>{
      if(die_value_cent.second_cent === null){
        die_value_cent.second_cent=0.0;
      }else{
      die_value_cent.second_cent=(parseFloat(die_value_cent.second_cent) + 0.01).toFixed(2);
      }
    }

    const die_second_cent_subtract = () => {
      if (die_value_cent.second_cent !== null && parseFloat(die_value_cent.second_cent) > 0.00) {
        die_value_cent.second_cent = (parseFloat(die_value_cent.second_cent) - 0.01).toFixed(2);
      }
    }
</script>

<template>
  <div id="app" style="background-color:#DCDCDC;">

    <div id="headetitle" style="background-color: white;" >
      <el-row>
        <el-col>
          <el-button><</el-button>
        </el-col>
      </el-row>
    </div>

    <div id="sreach1" class="block" >
      <el-row  justify="center" >
        <el-button  style="border: none;color: gray;" @click="sreach">请选择股票/基金/可转债</el-button>
      </el-row>
      <el-row  justify="center">
        <hr style="width:60vw;margin-top:1px;margin-bottom:1px">
      </el-row>
      <el-row  justify="center">
        <el-col :span="24">
          <p style="font-size: 15px;font-weight: 700;margin-top:1px;margin-bottom:1px" v-for="value in details.list">
              当前价{{ value.price }} 涨跌幅{{ value.price_limit }} 波动率{{ value.fluctuation }}
              <el-button @click="tips" style="width:10px;color:white; background-color: orangered;border:none">?</el-button> 
          </p>
        </el-col>
      </el-row>
    </div>
  
    <div id="date" class="block"  style="padding: 10px;">
        <!-- 日期范围行 -->
        <el-row class="date-row" >
          <el-col :span="5" class="label" justify="start" style="padding-top: 5px;">日期范围</el-col>
          <el-col :span="18" justify="start">
            <div style="display: flex; justify-content: space-evenly; align-items: center;">
              <el-date-picker
                id="oldday"
                v-model="startDate"
                type="date"
                placeholder="开始日期"
                style="width: 30vw;"
              />
              <span>到</span>
              <el-date-picker
                id="newday"
                v-model="endDate"
                type="date"
                placeholder="结束日期"
                style="width: 30vw;"
              />
            </div>
          </el-col>
        </el-row>
    
        <!-- 快捷选择行 -->
        <el-row class="quick-select-row" justify="start" style="padding-top: 5px;">
          <el-col :span="5" class="label" style="padding-top: 5px;">快捷选择</el-col>
          <el-col :span="18" >
            <div>
              <el-button style="width: 10vw;" @click="setDateRange(3)">近3月</el-button>
              <el-button style="width: 10vw;" @click="setDateRange(6)">近6月</el-button>
              <el-button style="width: 10vw;" @click="setDateRange(12)">近1年</el-button>
              <el-button style="width: 10vw;" @click="setDateRange(24)">近2年</el-button>
              <el-button style="width: 10vw;" @click="setDateRange(36)">近3年</el-button>
            </div>
          </el-col>
        </el-row>
    </div>

    <div id="condition" class="block" >
        <h3 style="text-align: left;background-color:#DCDCDC;padding-bottom:10px">触发条件</h3>
          <!-- 价格区间 -->
          <el-row class="price-row" >
            <el-col :span="5" justify="start" style="padding-top: 5px;">
              价格区间
            </el-col>
            <el-col :span="16">
              <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 5px;">
                <el-input style="width: 25vw" id="lowest" placeholder="最低价（元）"/>
                <div style="text-align:center;">~</div>
                <el-input style="width: 25vw" id="highest" placeholder="最高价（元）"/>
              </div>
            </el-col>
          </el-row>
      
          <!-- 触发基准价 -->
          <el-row class="trigger-row" justify="start" style="padding-top: 5px;padding-bottom:5px">
            <el-col :span="6"  style="padding-top: 5px;">
              触发基准价
            </el-col>
            <el-col :span="16" justify="start">
              <el-input style="width: 50vw;" id="triggerPrice" placeholder="请输入触发基准价（元）"/>
            </el-col>
          </el-row>
    </div>

    <div id="zhangdie_title" class="block" >
      <el-row class="block" style="padding:5px 5px 5px 5px;">
        <el-col :span="6" style="font-size:x-small;text-align:left;padding-left:5px">
          涨跌类型<br>(网格间距)
        </el-col>
        <el-col :span="12">
          <div v-show="zhangdie.show" style="font-size:15px;text-align:left;padding-top:5px">
            按百分比设置网格间距
          </div>
          <div v-if="!zhangdie.show" style="font-size:15px;text-align:left; padding-top:5px">
            按差价设置网格间距
          </div>
        </el-col>
        <el-col :span="6">
          <el-button style="width:70px;border: none;" v-show="zhangdie.show" @click="show_change">⇋按差价</el-button>
          <el-button style="width:70px;border: none;" v-if="!zhangdie.show" @click="show_change">⇋按百分比</el-button>
        </el-col>
      </el-row>
  
      <!-- 上涨... -->
      <el-row class="block">
        <el-col :span="5" style="font-size:13px;text-align:left;">
          <p>上涨...</p>
          <p v-show="zhangdie.huiluomaichu_show" style="font-size:x-small;color:orangered">卖出一格</p>
        </el-col>
        <el-col :span="3" class="down" >
          <el-button v-if="!zhangdie.show" @click="value_subtract">-</el-button>
          <el-button v-show="zhangdie.show" @click="cent_subtract">-</el-button>
        </el-col>
        <el-col :span="7" class="down">
          <el-input v-model="zhangdie_value_cent.first_cent" v-show="zhangdie.show"  placeholder="百分比（%）"></el-input>
          <el-input v-model="zhangdie_value_cent.first_value" v-if="!zhangdie.show"  placeholder="价格（元）"></el-input>
        </el-col>
        <el-col :span="3" class="down">
          <el-button v-if="!zhangdie.show" @click="value_add">+</el-button>
          <el-button v-show="zhangdie.show" @click="cent_add">+</el-button>
        </el-col>
        <el-col :span="6" class="down">
          <el-switch
              v-model="zhangdie.huiluomaichu_show"       
              style="--el-switch-on-color: #00BFFF; --el-switch-off-color: #FF4500"
            />
          <p style="font-size:x-small;">回落卖出</p>
        </el-col>
      </el-row>
  
      <!-- 回落... -->
      <el-row class="block" v-if="!zhangdie.huiluomaichu_show" >
        <el-col :span="5" style="font-size:13px;text-align:left;">
          <p>回落...</p>
          <p style="font-size:x-small;color:orangered">卖出一格</p>
        </el-col>
        <el-col :span="3" class="down" >
          <el-button v-show="zhangdie.show" @click="second_cent_subtract">-</el-button>
          <el-button v-if="!zhangdie.show" @click="second_value_add">-</el-button>
        </el-col>
        <el-col :span="13" class="down">
          <el-input v-model="zhangdie_value_cent.second_cent" v-show="zhangdie.show"  placeholder="百分比（%）"></el-input>
          <el-input v-model="zhangdie_value_cent.second_value" v-if="!zhangdie.show"  placeholder="价格（元）"></el-input>
        </el-col>
        <el-col :span="3" class="down">
          <el-button v-show="zhangdie.show" @click="second_cent_add">+</el-button>
          <el-button v-if="!zhangdie.show" @click="second_value_subtract">+</el-button>
        </el-col>
      </el-row>
  
      <!-- 下跌... -->
      <el-row class="block">
        <el-col :span="5" style="font-size:13px;text-align:left;">
          <p>下跌...</p>
          <p v-show="zhangdie.guaidianmairu_show" style="font-size:x-small;color:green">买入一格</p>
        </el-col>
        <el-col :span="3" class="down">
          <el-button v-if="!zhangdie.show" @click="die_value_add">-</el-button>
          <el-button v-show="zhangdie.show" @click="die_cent_add">-</el-button>
        </el-col>
        <el-col :span="7" class="down">
          <el-input v-model="die_value_cent.first_cent" v-show="zhangdie.show"  placeholder="百分比（%）"></el-input>
          <el-input v-model="die_value_cent.first_value" v-if="!zhangdie.show"  placeholder="价格（元）"></el-input>
        </el-col>
        <el-col :span="3" class="down">
          <el-button v-if="!zhangdie.show" @click="die_value_subtract">+</el-button>
          <el-button v-show="zhangdie.show" @click="die_cent_subtract">+</el-button>
        </el-col>
        <el-col :span="6" class="down">
          <el-switch
              v-model="zhangdie.guaidianmairu_show"       
              style="--el-switch-on-color: #00BFFF; --el-switch-off-color: #FF4500"
            />
          <p style="font-size:x-small;">拐点买入</p>
        </el-col>
      </el-row>
  
      <!-- 反弹... -->
      <el-row class="block" v-if="!zhangdie.guaidianmairu_show" >
        <el-col :span="5" style="font-size:13px;text-align:left;">
          <p>反弹...</p>
          <p style="font-size:x-small;color:green">买入一格</p>
        </el-col>
        <el-col :span="3" class="down" >
          <el-button v-show="zhangdie.show" @click="die_second_cent_subtract">-</el-button>
          <el-button v-if="!zhangdie.show" @click="die_second_value_subtract">-</el-button>
        </el-col>
        <el-col :span="13" class="down">
          <el-input v-model="die_value_cent.second_cent" v-show="zhangdie.show"  placeholder="百分比（%）"></el-input>
          <el-input v-model="die_value_cent.second_value" v-if="!zhangdie.show"  placeholder="价格（元）"></el-input>
        </el-col>
        <el-col :span="3" class="down">
          <el-button v-show="zhangdie.show" @click="die_second_cent_add">+</el-button>
          <el-button v-if="!zhangdie.show" @click="die_second_value_add">+</el-button>
        </el-col>
      </el-row>
    </div>

    <div id="condition" class="block"  >
      <h3 style="text-align: left;background-color:#DCDCDC;padding-bottom:10px">委托设置</h3>
        <!-- 委托类型 -->
    <el-row class="block" >
      <el-col :span="6">委托类型</el-col>
      <el-col :span="9" style="text-align: left;"> 
        <el-radio  v-model="isChecked1" @click="handleChange">按股数</el-radio>
      </el-col>
      <el-col :span="9" style="text-align: left;">
        <el-radio  v-model="isChecked2" @click="handleChange0">按金额</el-radio>
      </el-col>
    </el-row>

    <!-- 网络类型 -->
    <el-row class="block" >
      <el-col :span="6">网络类型</el-col>
      <el-col :span="9" style="text-align: left;">
        <el-radio v-model="isChecked3" @change="handleChange1('isChecked3')">对称网络</el-radio>
      </el-col>
      <el-col :span="9" style="text-align: left;">
        <el-radio v-model="isChecked4" @change="handleChange1('isChecked4')">不对称网络</el-radio>
      </el-col>
    </el-row>

    <!-- 每笔委托 -->
    <el-row class="block" v-show="display1">
      <el-col :span="6">每笔委托</el-col>
      <el-col :span="18">
        <el-input placeholder="股数（股）" v-show="entrust_gu.show" v-model="entrust_gu.value" style="border: none;"></el-input>
        <el-input placeholder="金额（元）" v-show="entrust_vlaue.show" v-model="entrust_vlaue.value" style="border: none;"></el-input>
      </el-col>
    </el-row>

    <!-- 每笔买入 -->
    <el-row class="block" v-if="!display1">
      <el-col :span="6" >每笔买入</el-col>
      <el-col :span="18" >
        <el-input placeholder="股数（股）" v-show="entrust_gu.show" v-model="pingheng_entrust_vlaue.value" style="border: none;"></el-input>
        <el-input placeholder="金额（元）" v-show="entrust_vlaue.show" v-model="pinghengentrust_gu.value" style="border: none;"></el-input>
      </el-col>
    </el-row>

    <!-- 每笔卖出 -->
    <el-row class="block" v-if="!display1">
      <el-col :span="6">每笔卖出</el-col>
      <el-col :span="18">
        <el-input placeholder="股数（股）" v-show="entrust_gu.show" v-model="pingheng_entrust_vlaue.value" style="border: none;"></el-input>
        <el-input placeholder="金额（元）" v-show="entrust_vlaue.show" v-model="pinghengentrust_gu.value" style="border: none;"></el-input>
      </el-col>
    </el-row>
      <div style="text-align: left;background-color:#DCDCDC;padding-bottom:10px">
        <el-row >
          <el-col :span="1.5">
            <el-switch style="padding-top:12px ;" v-model="switch1" disabled/>
          </el-col>
          <el-col :span="12">
            <p>倍数委托已开启</p>
          </el-col>
        </el-row>
          <p style="color: orangered; text-align:left">*很重要，不可关闭！开启后，当行情突然暴涨，网格会一次性卖出多个，否则只能卖出一格（错失最佳的卖出点位）</p>
        </div>
    </div>

    <div id="setting" class="block" >
      <h3 style="text-align: left;background-color:#DCDCDC;padding-bottom:10px">高级设置</h3>
        <el-row style="padding-left:10px;padding-top:0">
          <el-col :span="1.5">
            <el-switch style="padding-top:12px ;" v-model="switch2" />
          </el-col>
          <el-col :span="15">
            <p>是否为顶部清仓中枢建仓模式</p>
          </el-col>
        </el-row>
        <el-row style="padding-left:10px">
          <p style="text-align:left;color:gray;font-size: x-small;">当标的超出网格上限，卖出全部仓底，进去待重启状态，跌回网格中枢后，重启网格继续运行。</p>
        </el-row>
    </div>

  </div>
</template>

<style  scoped>

  .date_grid{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
    column-gap:auto;
  }
  
  .block{
    text-align: center;
    background-color:white;
    margin:10px 10px 10px 10px;
    padding: 0;
  }

  .down{
    padding-top:5px
  }
</style>