## Welcome to GitHub Pages

<html>
     <head><title>new web</title></head>
     <body background="file:///C:/Users/user/Desktop/%E4%BB%A3%E7%A0%81%E7%85%A7%E7%89%87/%E3%80%821.PNG">
     <table background="file:///C:/Users/user/Desktop/58PIC6d58PICxQC_1024.jpg!qt324"  width="100%" height="20%" border="1">
           <tr>
           <td width="6s0%"><pre><p style="font-size:40px">               welcome to my website     </pre></p></td>
           <td width="40%"><h2><script type="text/javascript">  
         function show(){ 
         var date = new Date(); //日期?象 
         var now = ""; 
         now = date.getFullYear()+"-"; //?英文就行了 
         now = now + (date.getMonth()+1)+"-"; //取月的?候取的是?前月-1如果           想取?前月+1就可以了 
	 now = now + date.getDate()+":"; 
	 now = now + date.getHours()+":"; 
	 now = now + date.getMinutes()+":"; 
	 now = now + date.getSeconds()+""; 
	 document.getElementById("nowDiv").innerHTML = now; //div的html是now	 ??字符串 
	 setTimeout("show()",1000); //?置?1000毫秒就是1秒，?用show方法 
	 } 
	 </script> 
	 <body onload="show()"> <!-- 网?加???用一次 以后就自??用了--> 
	 <div id="nowDiv"></div> 
 	 </body></h2>
           </td>
           </tr>
     </table> 
       
<meta charset="UTF-8">
<title>Calendar</title>
<style type="text/css">
body{
	background:#f2f2f2;
	margin:40px;
}
*{
	margin:0;
	padding:0;
}
.calendar{
	width:450px;
	height:350px;
	background:#fff;
	box-shadow:0px 1px 1px rgba(0,0,0,0.1);
}
.title{
	height:70px;
	border-bottom:1px solid rgba(0,0,0,0.1);
	text-align:center;
	position:relative;
}
#calendar-title{
	font-size:25px;
	font-family:arial;
	font-weight:bold;
	text-transform:uppercase;
	padding:14px 0 0 0;
}
#calendar-year{
	font-size:15px;
	font-family:arial;
	font-weight:normal;
}
#prev{
	text-indent:-9999px;
	position:absolute;
	left:0;
	top:0;
	width:60px;
	height:70px;
	background:url(prev.png) no-repeat 50% 50%;
}
#next{
	text-indent:-9999px;
	position:absolute;
	right:0;
	top:0;
	width:60px;
	height:70px;
	background:url(next.png) no-repeat 50% 50%;
}
.body{
	padding:10px 20px;
}
.body-list ul{
	width:100%;
	font-family:arial;
	font-weight:bold;
	font-size:14px;
}
.body-list ul li{
	width:14.28%;
	height:36px;
	line-height:36px;
	list-style-type:none;
	display:block;
	box-sizing:border-box;
	float:left;
	text-align:center;
}
.lightgrey{
	color:#a8a8a8;
}
.darkgrey{
	color:#565656;
}
.green{
	color:#6ac13c;
}
.greenbox{
	border:1px solid #6ac13c;
	background:#e9f8df;
}
</style>
</head>

<body>
<div class="calendar">
  <div class="title">
    <h1 class="green" id="calendar-title">Month</h1>
    <h2 class="green small" id="calendar-year">Year</h2>
    <a href="" id="prev">Prev Month</a>
    <a href="" id="next">Next Month</a>
  </div>
  <div class="body">
    <div class="lightgrey body-list">
      <ul>
        <li>MON</li>
        <li>TUE</li>
        <li>WED</li>
        <li>THU</li>
        <li>FRI</li>
        <li>SAT</li>
        <li>SUN</li>
      </ul>
    </div>
    <div class="darkgrey body-list">
      <ul id="days">
      </ul>
    </div>
  </div>
</div>
<script type="text/javascript">
var month_olympic = [31,29,31,30,31,30,31,31,30,31,30,31];
var month_normal = [31,28,31,30,31,30,31,31,30,31,30,31];
var month_name = ["January","Febrary","March","April","May","June","July","Auguest","September","October","November","December"];
var holder = document.getElementById("days");
var prev = document.getElementById("prev");
var next = document.getElementById("next");
var ctitle = document.getElementById("calendar-title");
var cyear = document.getElementById("calendar-year");
var my_date = new Date();
var my_year = my_date.getFullYear();
var my_month = my_date.getMonth();
var my_day = my_date.getDate();
prev.onclick = function(e){
	e.preventDefault();
	my_month--;
	if(my_month<0){
		my_year--;
		my_month = 11;
	}
	refreshDate();
}
next.onclick = function(e){
	e.preventDefault();
	my_month++;
	if(my_month>11){
		my_year++;
		my_month = 0;
	}
	refreshDate();
}
function refreshDate(){
	var str = "";
	var totalDay = daysMonth(my_month, my_year); //?取?月?天?
	var firstDay = dayStart(my_month, my_year); //?取?月第一天是星期几
	var myclass;
	for(var i=1; i<firstDay; i++){ 
		str += "<li></li>"; //?起始日之前的日期?建空白??
	}
	for(var i=1; i<=totalDay; i++){
		if((i<my_day && my_year==my_date.getFullYear() && my_month==my_date.getMonth()) || my_year<my_date.getFullYear() || ( my_year==my_date.getFullYear() && my_month<my_date.getMonth())){ 
			myclass = " class='lightgrey'"; //??日期在今天之前?，以?灰色字体?示
		}else if (i==my_day && my_year==my_date.getFullYear() && my_month==my_date.getMonth()){
			myclass = " class='green greenbox'"; //??日期是?天?，以?色背景突出?示
		}else{
			myclass = " class='darkgrey'"; //??日期在今后之后?，以深灰字体?示
		}
		str += "<li"+myclass+">"+i+"</li>"; //?建日期??
	}
	holder.innerHTML = str; //?置日期?示
	ctitle.innerHTML = month_name[my_month]; //?置英文月份?示
	cyear.innerHTML = my_year; //?置年份?示
}
//?取某年某月第一天是星期几
function dayStart(month, year) {
	var tmpDate = new Date(year, month, 1);
	return (tmpDate.getDay());
}

//?算某年是不是?年，通?求年份除以4的余?即可
function daysMonth(month, year) {
	var tmp = year % 4;
	if (tmp == 0) {
		return (month_olympic[month]);
	} else {
		return (month_normal[month]);
	}
}
refreshDate();
</script>
         <h1><table border="1" width="50%" height="20%" background="file:///C:/Users/user/Desktop/%E4%B8%8B%E8%BC%89.jpg">
              <tr>
              <th><p style="font-size:40px">this is my recording</p></th>
              <td><p style="font-size:40px"><a href="recording">click</a></p></td>
              </tr>
              <tr>
              <th><p style="font-size:40px">this is my vedio</p></th>
              <td><p style="font-size:40px"><a href="vedio.html">click</a></p></td>
              </tr>
         </table></h1>
              <hr>
         <table border="1" width="100%" height="20%">
              <tr>
              <td width="33.3%"><a href="https://www.youtube.com/watch?v=UvFISD1nffE">
                  <img src="file:///F:/%E7%BD%91%E9%A1%B5/%E3%80%821.PNG"/ height="50%" width="50%"/>
                  </a>
              </td>
              <td width="33.3%"><a href="https://www.youtube.com/watch?v=damn7ju8BO0">
                  <img src="file:///C:/Users/Student/Desktop/%E4%B8%8B%E8%BC%89.jpg" height="30%" width="30%"/>
                  </a>
                  
              </td>
              <td width="33.3%"><a href="https://www.youtube.com/watch?v=pZgHa2yj9Mk">
                  <img src="file:///C:/Users/user/Desktop/ASCII-maxresdefault.gif" height="50%" width="50%"/>
                  </a>
              </td>
              </tr>
         </table>
              <hr>
      </body>
</html>

