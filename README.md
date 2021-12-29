Skip to content
Search or jump to…
Pull requests
Issues
Marketplace
Explore
 
@qiziyue99 
qiziyue99
/
qiziyue99.github.io
Public
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
qiziyue99.github.io/index.html
@qiziyue99
qiziyue99 网页托管
Latest commit 7a6862a 1 minute ago
 History
 1 contributor
463 lines (416 sloc)  15.8 KB
   
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta name="description" content="小兔鲜儿官网，致力于打造全球最大的食品、生鲜电商购物平台">
        <meta name="keywords" content="小兔鲜儿,食品,生鲜,服装,家电,电商,购物">
		<title>小兔鲜儿-新鲜、惠民、快捷！</title>
		
        
        <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
        <link rel="stylesheet" href="./css/base.css">
        <link rel="stylesheet" href="./css/common.css">
        <link rel="stylesheet" href="./css/index.css">
		
		<!--引用工具-->
		<script type="text/javascript" src="js/tools.js"></script>
		<script type="text/javascript">
			window.onload = function(){
				//获取imgList
				var imgList = document.getElementById("imgList");
				//获取页面中所有的img标签
				var imgArr = imgList.getElementsByTagName("img");
				//设置imgList的宽度
				imgList.style.width = 1260*imgArr.length+"px";
				
				
				/*设置导航按钮居中*/
				//获取navDiv
				var navDiv = document.getElementById("navDiv");
				//获取outer
				var outer = document.getElementById("outer");
				//设置navDiv的left值
				navDiv.style.left = (outer.offsetWidth - navDiv.offsetWidth)/2 + "px";
				
				//默认显示图片的索引
				var index = 0;
				//获取所有的a
				var allA = navDiv.getElementsByTagName("a");
				//设置默认选中的效果
				allA[index].style.backgroundColor = "black";
				
				/*
				 	点击超链接切换到指定的图片
				 		点击第一个超链接，显示第一个图片
				 		点击第二个超链接，显示第二个图片
				 * */
				
				//为所有的超链接都绑定单击响应函数
				for(var i=0; i<allA.length ; i++){
					
					//为每一个超链接都添加一个num属性
					allA[i].num = i;
					
					//为超链接绑定单击响应函数
					allA[i].onclick = function(){
						
						//关闭自动切换的定时器
						clearInterval(timer);
						//获取点击超链接的索引,并将其设置为index
						index = this.num;
						
						//切换图片
						/*
						 * 第一张  0 0
						 * 第二张  1 -520
						 * 第三张  2 -1040
						 */
						//imgList.style.left = -520*index + "px";
						//设置选中的a
						setA();
						
						//使用move函数来切换图片
						move(imgList , "left" , -1260*index , 20 , function(){
							//动画执行完毕，开启自动切换
							autoChange();
						});
						
					};
				}
				
				
				//开启自动切换图片
				autoChange();
				
				
				//创建一个方法用来设置选中的a
				function setA(){
					
					//判断当前索引是否是最后一张图片
					if(index >= imgArr.length - 1){
						//则将index设置为0
						index = 0;
						
						//此时显示的最后一张图片，而最后一张图片和第一张是一摸一样
						//通过CSS将最后一张切换成第一张
						imgList.style.left = 0;
					}
					
					//遍历所有a，并将它们的背景颜色设置为红色
					for(var i=0 ; i<allA.length ; i++){
						allA[i].style.backgroundColor = "";
					}
					
					//将选中的a设置为黑色
					allA[index].style.backgroundColor = "black";
				};
				
				//定义一个自动切换的定时器的标识
				var timer;
				//创建一个函数，用来开启自动切换图片
				function autoChange(){
					
					//开启一个定时器，用来定时去切换图片
					timer = setInterval(function(){
						
						//使索引自增
						index++;
						
						//判断index的值
						index %= imgArr.length;
						
						//执行动画，切换图片
						move(imgList , "left" , -1260*index , 20 , function(){
							//修改导航按钮
							setA();
						});
						
					},3000);
					
				}
				
				
			};
			
		</script>
	</head>
	<body>
		 <!-- 快捷导航 -->
         <div class="shortcut">
            <div class="wrapper">
                <ul>
                    <li><a href="#">请先登录</a></li>
                    <li><a href="#">免费注册</a></li>
                    <li><a href="#">我的订单</a></li>
                    <li><a href="#">会员中心</a></li>
                    <li><a href="#">帮助中心</a></li>
                    <li><a href="#">在线客服</a></li>
                    <li><a href="#"><span></span>手机版</a></li>
                </ul>
            </div>
        </div>
    
        <!-- 头部 -->
        <div class="header wrapper">
            <div class="logo">
                <h1><a href="#">小兔鲜儿</a></h1>
            </div>
            <div class="nav">
                <ul>
                    <li><a href="#">首页</a></li>
                    <li><a href="#">生鲜</a></li>
                    <li><a href="#">美食</a></li>
                    <li><a href="#">餐厨</a></li>
                    <li><a href="#">电器</a></li>
                    <li><a href="#">居家</a></li>
                    <li><a href="#">洗护</a></li>
                    <li><a href="#">孕婴</a></li>
                    <li><a href="#">服装</a></li>
                </ul>
            </div>
            <div class="search">
                <input type="text" placeholder="搜一搜">
                <!-- 定位 放大镜 -->
                <span></span>
            </div>
            <div class="car">
                <span>2</span>
            </div>
        </div>
        
        <!-- banner -->
        <div class="banner">
            <!-- 创建一个外部的div，来作为大的容器 -->
		<div id="outer">
			<!-- 创建一个ul，用于放置图片 -->
			<ul id="imgList">
				<li><a href="#"><img src="./uploads/banner_1.png"/></a></li>
				<li><a href="#"><img src="./uploads/banner_2.jpeg"/></a></li>
				<li><a href="#"><img src="./uploads/banner_3.jpeg"/></a></li>
				<li><a href="#"><img src="./uploads/banner_4.jpeg"/></a></li>
				<li><a href="#"><img src="./uploads/banner_5.jpeg"/></a></li>
				<li><a href="#"><img src="./uploads/banner_1.png"/></a></li>
			</ul>

             <!-- 侧导航 -->
             <div class="aside">
                <ul>
                    <li><a href="#">生鲜<span>水果蔬菜</span></a></li>
                    <li><a href="#">美食<span>面点干果</span></a></li>
                    <li><a href="#">餐厨<span>数码产品</span></a></li>
                    <li><a href="#">电器<span>床品 四件套 被枕</span></a></li>
                    <li><a href="#">居家<span>奶粉 玩具 辅食</span></a></li>
                    <li><a href="#">洗护<span>洗发 洗护 美妆</span></a></li>
                    <li><a href="#">孕婴<span>奶粉 玩具</span></a></li>
                    <li><a href="#">服饰<span>女装 男装</span></a></li>
                    <li><a href="#">杂货<span>户外 图书</span></a></li>
                    <li><a href="#">品牌<span>品牌制造</span></a></li>
                </ul>
            </div>

			<!--创建导航按钮-->
			<div id="navDiv">
				<a  href="javascript:;"></a>
				<a  href="javascript:;"></a>
				<a  href="javascript:;"></a>
				<a  href="javascript:;"></a>
				<a  href="javascript:;"></a>
			</div>

		</div>

        </div>
        

         <!-- 新鲜好物 -->
    <div class="goods wrapper">
        <!-- 头部 -->
        <div class="hd">
            <h2>新鲜好物<span>新鲜出炉 品质靠谱</span></h2>
            <a href="#">查看全部</a>
        </div>
        <!-- body 身体 -->
        <div class="bd clearfix">
            <ul>
                <li>
                    <a href="#">
                        <img src="./uploads/new_goods_1.jpg" alt="">
                        <h3>睿米无线吸尘器F8</h3>
                        <div>￥<span>899</span></div>
                        <b>新品</b>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/new_goods_2.jpg" alt="">
                        <h3>智能环绕3D空调</h3>
                        <div>￥<span>1299</span></div>
                        <b>新品</b>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/new_goods_3.jpg" alt="">
                        <h3>广东软软糯糯煲仔饭</h3>
                        <div>￥<span>129</span></div>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/new_goods_4.jpg" alt="">
                        <h3>罗西机械智能手表</h3>
                        <div>￥<span>3399</span></div>
                    </a>
                </li>

            </ul>
        </div>
    </div>

    <!-- 人气推荐 -->
    <div class="popular wrapper">
        <!-- 头部 -->
        <div class="hd">
            <h2>人气推荐<span>人气推荐 不容错过</span></h2>
        </div>
        <!-- body 身体 -->
        <div class="bd clearfix">
            <ul>
                <li>
                    <a href="#">
                        <img src="./uploads/popular_1.jpg" alt="">
                        <h3>特惠推荐</h3>
                        <span>我猜得到 你的需要</span>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/popular_2.jpg" alt="">
                        <h3>爆款推荐</h3>
                        <span>人气好物推荐</span>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/popular_3.jpg" alt="">
                        <h3>场景使用一站买全</h3>
                        <span>编辑精心整理推荐</span>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/popular_4.jpg" alt="">
                        <h3>领劵中心</h3>
                        <span>发现更多超值优惠券</span>
                    </a>
                </li>

            </ul>
        </div>
    </div>

    <!-- 热门品牌 -->
    <div class="brand wrapper">
        <!-- 头部 -->
        <div class="hd">
            <h2>热门品牌<span>国际经典 品质保证</span></h2>
        </div>
        <!-- body 身体 -->
        <div class="bd clearfix">
            <ul>
                <li>
                    <a href="#">
                        <img src="./uploads/brand_goods_1.jpg" alt="">
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/brand_goods_2.jpg" alt="">
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/brand_goods_3.jpg" alt="">
                    </a>
                </li>
                <li>
                    <a href="#">
                        <img src="./uploads/brand_goods_4.jpg" alt="">
                    </a>
                </li>

            </ul>
        </div>
    </div>

    <!-- 生鲜 -->
    <div class="shengxian wrapper">
        <div class="hd">
            <h2>生鲜</h2>
            <a href="#" class="more">查看全部</a>
            <ul>
                <li><a href="#">水果</a></li>
                <li><a href="#">蔬菜</a></li>
                <li><a href="#">肉禽蛋</a></li>
                <li><a href="#">裤装</a></li>
                <li><a href="#">衬衫</a></li>
                <li><a href="#">T恤</a></li>
                <li><a href="#">内衣</a></li>
            </ul>
        </div>
        <div class="bd clearfix">
            <div class="left">
                <a href="#"><img src="./uploads/fresh_goods_cover.png" alt=""></a>
            </div>
            <div class="right">
                <ul class="top">
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_1.jpg">
                        <h3>美威 智利原为三文鱼排</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_2.jpg">
                        <h3>红功夫 麻辣小龙虾</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_3.jpg">
                        <h3>三都港 冷冻无公害黄花鱼</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_4.jpg">
                        <h3>渔公码头 大连鲜食入味</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                </ul>
                <ul class="bottom">
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_5.jpg">
                        <h3>美威 智利原为三文鱼排</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_6.jpg">
                        <h3>红功夫 麻辣小龙虾</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_7.jpg">
                        <h3>三都港 冷冻无公害黄花鱼</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                        <img src="./uploads/fresh_goods_8.jpg">
                        <h3>渔公码头 大连鲜食入味</h3>
                        <div>￥<span>59</span></div>
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </div>

    <!-- 版权区域 -->
    <div class="footer">
        <div class="wrapper">
            <div class="top">
                <ul>
                    <li>
                        <span>价格亲民</span>
                    </li>
                    <li>
                        <span>物流快捷</span>
                    </li>
                    <li>
                        <span>品质新鲜</span>
                    </li>
                </ul>
            </div>
            <div class="bottom">
                <p>
                    <a href="#">关于我们</a> |
                    <a href="#">帮助中心</a> |
                    <a href="#">售后服务</a> |
                    <a href="#">配送与验收</a> |
                    <a href="#">商务合作</a> |
                    <a href="#">搜索推荐</a> |
                    <a href="#">友情链接</a>
                </p>
                <p>CopyRight @ 小兔鲜儿</p>
            </div>
        </div>
    </div>
	</body>
</html>
