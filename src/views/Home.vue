<template>
	<div class="mainContent">

		<!-- 头部导航栏及轮播图部分 -->
		<el-row class="grid-content-background">
		 <div class="content-main-menban" :style="{backgroundImage:backImg,
			backgroundSize:backSize,
			backgroundPosition:backPs,
			backgroundRepeat:backRep,
			paddingBottom:backPad,
		 	transition:trans}">

		 </div>
		 <el-menu :default-active="activeIndex2" class="el-menu-demo" mode="horizontal" @select="handleSelect">
			 <el-menu-item index="1">我的简介</el-menu-item>
		 </el-menu>
		 <!-- 轮播图banner -->
		  <el-col :span="24">
				<div class="content">
					<el-row>
						<el-col :span="9" class="content-leftCol">
							<el-card class="content-user-img">
								<el-carousel  :interval="8000" trigger="click"  height="487px" @change="change($event)">
									<el-carousel-item v-for="item in item">
										 <h3>
												 <img :src="item.src">
										 </h3>
									</el-carousel-item>
								</el-carousel>
								<p :style="{color:itempColor}" class="itemP">{{itemP}}</p>
			 			 </el-card>
						</el-col>
						<el-col :span="15">
							<el-row>
								<el-col :span="1">
									<div class="zhanwei"></div>
								</el-col>
								<el-col :span="22" class="content-rightCol">
									<p class="content-rightCol-p">我的Blog</p>
									<el-badge is-dot class="content-rightCol-item">
									  <el-button class="share-button" icon="share" type="primary">互联网</el-button>
									</el-badge>
									<p class="company-p">所属公司:<span style="color:#6666ff;cursor:pointer;margin-left:10px;">{{ownCompany}}</span></p>
									<p><span class="payMoney">{{payMoney}}</span>元起购</p>
									<!-- 表单展示开始 -->
									<form>
										<table border="1" class="company_list">
											<tbody>
												<tr>
													<th>姓名</th>
													<th>黄建</th>
													<th>性别</th>
													<th>男</th>
												</tr>
												<tr>
													<th>学历</th>
													<th>专科</th>
													<th>毕业学校</th>
													<th>四川工程职业技术学院</th>
												</tr>
												<tr>
													<th>婚配</th>
													<th>未婚</th>
													<th>专业</th>
													<th>计算机应用</th>
												</tr>
												<tr>
													<th>家庭住址</th>
													<th>成都市高新西区</th>
													<th>爱好</th>
													<th>睡觉</th>
												</tr>
												<tr>
													<th>工作时间</th>
													<th>2年</th>
													<th></th>
													<th></th>
												</tr>
											</tbody>
										</table>
									</form>
									<!-- 表单展示结束 -->

										<el-badge :value="clicked" class="getItButton">
											<el-button type="primary" @click="addClicked" class="getButton">
													Get It!
											</el-button>
										</el-badge>

								</el-col>
							</el-row>
						</el-col>
					</el-row>

				</div>
		  </el-col>

		</el-row>
		<!-- content部分 -->
		<div class="upper-content">
			<!-- 个人项目模块 -->
			<div class="upper-content-myProjrct">

				<div class="myProject-content  box-regular">
					<p class="normalTitle">My Project</p>
					<p class="normalDescript">穷极上半身精力，励精图治，殚精竭血，完成了各个挑战！</p>

					<div class="flex-box">
						<el-card class="normalCard" v-for="item in myProjects">
							<div class="normalCardImg">
								<img :style="{backgroundImage:item.projSrc}">
							</div>
							<span>{{item.projName}}</span>
							<div>
								<time class="time">{{ item.currentDate }}</time>
								<el-button type="primary" class="projButton" icon="search">了解一哈</el-button>
							</div>
						</el-card>
					</div>
				</div>

			</div>

			<!-- 个人技能模块 -->

			<div class="upper-content-mySkill">
				<div class="mySkill-content box-regular">
					<p class="normalTitle">VueJs 组件案例库</p>
					<p class="normalDescript">你想知道生命的真正意义吗？
						<el-button-group class="centerBox">
						  <el-button type="primary" @click="jumpToHell()">yes</el-button>
						  <el-button type="primary" :disabled="true">no</el-button>
						</el-button-group>
					</p>

					<el-row class="projBox">
						<el-card>
						<!-- 左边栏存放案例实际效果 -->
						<el-col :span="12">
							<div class="echarts">
						    <button @click="doRandom">Random</button>
						  </div>
						</el-col>
						<!-- 右边栏存放案例解析 -->
						<el-col :span="12">

						</el-col>
						</el-card>
					</el-row>
					<!-- 时间选择组件 -->
					<el-row class="projBox">
						<el-card>
						<!-- 左边栏存放案例实际效果 -->
						<el-col :span="12">
							<TimePicker></TimePicker>
						</el-col>
						<!-- 右边栏存放案例解析 -->
						<el-col :span="12">
							<div class="projDesc">
								<p>组件名：基于Vue2的时间选择组件</p>
								<p>组件功能：实现Vue2与TimePicker的互通,结合了Element Ui,vuex及vue-router实现...</p>
							</div>
						</el-col>
						</el-card>
					</el-row>
					<!-- 时间选择组件2 -->
					<el-row class="projBox">
						<el-card>
						<!-- 左边栏存放案例实际效果 -->
						<el-col :span="12">
							<DatePicker></DatePicker>
						</el-col>
						<!-- 右边栏存放案例解析 -->
						<el-col :span="12">
							<div class="projDesc">
								<p>组件名：基于Vue2的时间选择组件</p>
								<p>组件功能：实现Vue2与TimePicker的互通,结合了Element Ui,vuex及vue-router实现...</p>
							</div>
						</el-col>
						</el-card>
					</el-row>
					<!-- 进度条组件 -->
					<el-row class="projBox">
						<el-card>
						<!-- 左边栏存放案例实际效果 -->
						<el-col :span="12">
							<Progress></Progress>
						</el-col>
						<!-- 右边栏存放案例解析 -->
						<el-col :span="12">
							<div class="projDesc">
								<p>组件名：基于Vue2的进度条展示组件</p>
								<p>组件功能：实现Vue2与Progress的互通,结合了Element Ui,vuex及vue-router实现...</p>
							</div>
						</el-col>
						</el-card>
					</el-row>


					<el-button type="primary" icon="share" class="learnMoreBth" @click="learnMore()">了解更多</el-button>

				</div>
			</div>

		</div>

		<footer>
			<div class="box-regular">
				<p class="footer-title">Modoule make things different!</p>
				<div class="outer-box">
					<div class="pd-box">
						<div class="flex-box transform-box">
							<el-button type="primary" :autofocus=true><i class="el-icon-plus"></i> Vue Mode </el-button>
							<el-button type="primary"><i class="el-icon-plus"></i> React Mode </el-button>
							<el-button type="primary"><i class="el-icon-plus"></i> Angular Mode </el-button>
						</div>
					</div>
				</div>

			</div>

		</footer>
	</div>

</template>
<script src="./../common/js/jquery-1.10.2.min.js" charset="utf-8"></script>
<script src="./../common/js/lazyload.min.js" charset="utf-8"></script>
<script>
import animate from "animate.css";
import TimePicker from './components/timeDatePicker.vue';
import DatePicker from './components/datePicker.vue';
import Progress from './components/progress.vue';
export default {
		name: 'view',
    components: {
    
		TimePicker,
		DatePicker,
		Progress
    },
    data() {
      return {
				activeIndex: '1',
        activeIndex2: '1',
        activeName: 'first',
				logo:'http://chuantu.biz/t5/52/1490604209x2728329016.png',
				backImg:'url("http://img0.imgtn.bdimg.com/it/u=1766782369,881046989&fm=23&gp=0.jpg")',
				backPad:'50px',
				backSize:'100%',
				backPs:'center',
				backRep:'no-repeat',
				trans:'all linear .5s',
				payMoney:'8000',
				getEd:true,
				aNum:0,
				ownCompany:'成都悠唐网络科技有限公司',
				clicked:0,
				itempColor:'',
				itemP:'',
				loading:true,
				item:[
						{
							src:'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1490702808235&di=96ac8454a85fa927204c889b1a319ee9&imgtype=0&src=http%3A%2F%2Fimg4.duitang.com%2Fuploads%2Fitem%2F201112%2F31%2F20111231190234_GXff5.thumb.700_0.jpg',
							p:'asdasd',
							pColor:'red'
						},
						{
							src:'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1490702830652&di=9407696de959d2a441b07cf4278f6e63&imgtype=0&src=http%3A%2F%2Fimg0.ph.126.net%2FR8tsOWYEFokKZN8tFw10VA%3D%3D%2F6598164880238302173.jpg',
							p:'asdasd',
							pColor:'black'
						},
						{
							src:'http://www.818hr.cn/uploadfile/2015/0112/20150112040817888.jpg',
							p:'asdasd',
							pColor:'orange'
						},
					],
				myProjects:[
					{
						projSrc:'url("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1491376221&di=359f4eb38854c8ea51eed6647f7db109&imgtype=jpg&er=1&src=http%3A%2F%2Fimages.17173.com%2F2014%2Fnews%2F2014%2F04%2F29%2Fhy0429lq02s.jpg")',
						projName:"第一个项目",
						currentDate:this.computeDate(),
					},
					{
						projSrc:'url("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1490781640486&di=8f9e59ef59d9342e6b689535d453eca9&imgtype=0&src=http%3A%2F%2Fimages.17173.com%2F2015%2Fnews%2F2015%2F02%2F10%2Fmj0210bq03s.jpg")',
						projName:"第二个项目",
						currentDate:this.computeDate(),
					},
					{
						projSrc:'url("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1491376221&di=359f4eb38854c8ea51eed6647f7db109&imgtype=jpg&er=1&src=http%3A%2F%2Fimages.17173.com%2F2014%2Fnews%2F2014%2F04%2F29%2Fhy0429lq02s.jpg")',
						projName:"第三个项目",
						currentDate:this.computeDate(),
					},
				],
      };
    },
		created:function(){
			console.log('创建之后！');
			this.aNum++;
			console.log("a",this.aNum);
		},
    methods: {
			jumpToHell(){
				window.open('http://blog.sina.com.cn/huangjianweb');
			},
			learnMore(){
				window.open('http://element.eleme.io/#/zh-CN/component/installation');
			},
			doRandom() {
        const that = this;
        let data = [];
        for (let i = 0, min = 5, max = 99; i < 6; i++) {
          data.push(Math.floor(Math.random() * (max + 1 - min) + min));
        }
        that.loading = !that.loading;
        that.bar.series[0].data = data;
      },
      onReady(instance) {
        console.log("123123",instance);
      },
      onClick(event, instance, echarts) {
        console.log(arguments);
      },
			computeDate(){
				 var date = new Date();
				 var seperator1 = "-";
				 var seperator2 = ":";
				 var month = date.getMonth() + 1;
				 var strDate = date.getDate();
				 if (month >= 1 && month <= 9) {
						 month = "0" + month;
				 }
				 if (strDate >= 0 && strDate <= 9) {
						 strDate = "0" + strDate;
				 }
				 var currentdate = date.getFullYear() + seperator1 + month + seperator1 + strDate
								 + " " + date.getHours() + seperator2 + date.getMinutes()
								 + seperator2 + date.getSeconds();
				 return currentdate;
			},
      handleClick(tab, event) {
        console.log(tab, event);
      },
			handleSelect(key, keyPath) {
			 console.log(key, keyPath);
		 	},
			change(event) {
				this.backImg = 'url("'+this.item[event].src+'")';
				this.itempColor = this.item[event].pColor;
				this.itemP = this.item[event].p;
			},
		  addClicked(){
				if(this.getEd){
					this.clicked++;
					this.getEd = false;
				}else{
					this.$notify.error({
					 title: '失败',
					 message: '你已经获取过一次了',
				 });
				}
		  }
    },
  };
</script>

<style scoped lang="scss">
	footer{
		height: 320px;
		background-color: #000;
	}
	.echarts {
    width: 400px;
    height: 400px;
  }
	p{
		margin: 0;
	}
	.zhanwei{
		width: 100%;
		height: 1px;
	}
	.boxSd{
		width: 100%;
		height: 100%;
	}
	.grid-content-main{
		border-bottom: 1px solid #d1dbe5;
		width: 100%;
		height: 41px;
		.content-main-img{
			background-color: transparent;
			height: 100%;
		}
	}

	.el-menu-demo{
		background-color: rgba(0,0,0,0);
		border: none;
		outline: none;
		.nav-logo{
			width: 100px;
			float: right;
			margin-right: 100px;
		}
	}
	.company_list{
		margin-top: 25px;
    border: 1px solid #f2f2f2;
    border-collapse: collapse;
	}
	.company_list tr{
		border-bottom:1px solid #f2f2f2;
	}
	.itemP{
		font-size: 30px;
		text-align: center;
		line-height: 80px;
	}
	.company_list tr th:nth-child(odd){
		background-color: #f9f9f9;
		font-size: 14px;
		color: #707070;
		font-weight: normal;
		width: 115px;
		height: 40px;
	}
	.company_list tr th:nth-child(even){
		background-color: rgba(255,255,255,.6);
		font-size: 14px;
		font-weight: normal;
		width: 180px;
	}
	.el-menu-item:hover{
		background-color: rgba(0,0,0,0);
	}
	.el-tabs__nav{
		margin-left: 200px;
	}
	.grid-content-background{
		height: 700px;
	}
	.content-main-menban{
		position: absolute;
		width: 100%;
		height: 700px;
		opacity: .3;
		min-width: 1260px;
	}

	.el-carousel__item h3 {
			position: relative;
			display: block;
			width: 100%;
			height: 100%;
	    color: #475669;
	    font-size: 14px;
	    opacity: 0.75;
	    line-height: 200px;
	    margin: 0;
	 }
	.content{
		padding-top: 40px;
		width: 1170px;
		height: 600px;
		margin: auto;
		.content-leftCol{
			height: 600px;
			border-right: 1px solid #ccc;
			.content-user-img{
				margin:auto;
				width: 400px;
				height: 600px;
			}
		}
		.content-rightCol{
			position: relative;
			.content-rightCol-p{
				float: left;
				font-size: 32px;
				color: #4d4d4d;
				font-family: 'microsoft yahei',
			}
			.el-button{
				padding: 6px 3px;
			}
			.content-rightCol-item{
				height: 30px;
				margin-top: 10px;
				margin-left: 10px;
				padding-bottom: 10px;
			}
			.company-p{
				margin: 30px 0;
			}
			.payMoney{
				color:orange;
				font-size: 34px;
				padding-right: 10px;
			}
			.getItButton{
				margin-top: 40px;
				.getButton{
					padding: 10px 20px;
				}
			}

		}
	}

	.box-regular{
		width: 1170px;
		margin: auto;
	}
	// 下半部content部分
	// 公共部分
	.normalTitle{
		padding-top: 40px;
		text-align: center;
		font-size: 34px;
		margin-top: 17px;
		margin-bottom: 20px;
	}
	.normalDescript{
		text-align: center;
		color: #656b6f;
	}
	// 公共部分结束
	.upper-content{
		margin-top: 50px;
		// 个人项目模块
		.upper-content-myProjrct{
			padding-bottom: 60px;
			background-color: #f9f9f9;
			.flex-box{
				display: flex;
				margin-top: 40px;
				justify-content: space-around;
				.normalCard{
					width: 320px;
					height: 440px;
					border: 1px solid #ccc;
					cursor: pointer;
					span{
						line-height: 40px;
					}
					.normalCardImg{
						width: 100%;
						height: 320px;
						img{
							width: 100%;
							height: 100%;
							background-size:cover;
							background-position: center;
							background-repeat: no-repeat;
						}
					}
				}
				.normalCard:hover{
					box-shadow: 1px 5px 50px 1px #ccc;
				}
			}
		}
		// 个人技能模块
		.upper-content-mySkill{
			padding-bottom: 60px;
		}
	}
	.learnMoreBth{
		margin: 40px 0 40px 500px;
	}
	.projButton{
		padding: 8px 10px;
		margin-left:44px;
	}
	.projBox{
		margin-top: 40px;
	}
	.projDesc{
		padding: 20px;
	}
	.footer-title{
		color: white;
		font-size: 34px;
		text-align: center;
		padding-top: 100px;
	}
	.outer-box{
		overflow: hidden;
		.pd-box{
			position: relative;
			float: left;
			left: 50%;
			.transform-box{
				padding-top: 80px;
				float: left;
				margin-left: -50%;
			}
		}
	}
		// 扩展组件
	.el-carousel__item h3 img{
		width: 100%;
		height: 100%;
	}
	 .el-carousel__item:nth-child(2n) {
	    background-color: #99a9bf;
	 }
	 .el-carousel__arrow{
		 background-color: rgba(0,0,0,1);
	 }
	 .el-carousel__item:nth-child(2n+1) {
	   background-color: #d3dce6;
	 }


</style>
