# Date-time
some date time 

js中时间


	var curDate = timeFormat(d);
	var preDate = timeFormat(new Date(d.getTime() - 24*60*60*1000));
	var firstDayOfMonth = getFirstDayOfMonth(d);
	var lastDayOfMonth = getLastDayOfMonth(d);
	var firstDayOfWeek = getFirstDayOfWeek();
	var lastDayOfWeek = getLastDayOfWeek();
	var firstDayOfQuarter = getQuarterStartDate();
	var lastDayOfQuarter = getQuarterEndDate();
	console.log("curDate="+curDate+" ;preDate="+preDate+" ;firstDayOfMonth="+firstDayOfMonth+"
	;lastDayOfMonth="+lastDayOfMonth+" ;firstDayOfWeek="+firstDayOfWeek+" ;lastDayOfWeek="+lastDayOfWeek + "
	;firstDayOfQuarter="+firstDayOfQuarter + " ;lastDayOfQuarter="+lastDayOfQuarter);
			

    //格式化日期
    function timeFormat(date) 
    {
       var y = date.getFullYear(); //年
       var m = date.getMonth() + 1; //月
       var d = date.getDate(); //日
       if(m < 10){   
           m = "0" + m;   
       }   
       if(d < 10){   
           d = "0" + d;   
       }   
       return y + "-" + m + "-" + d;
    }
	//获取这周的周一
	function getFirstDayOfWeek() 
	{
	    var date = new Date();
	    var weekday = date.getDay()||7; //获取星期几,getDay()返回值是 0（周日） 到 6（周六） 之间的一个整数。0||7为7，即weekday的值为1-7
	    date.setDate(date.getDate()-weekday+1);//往前算（weekday-1）天，年份、月份会自动变化
	    return timeFormat(date);
	}
	//获取这周的周末
	function getLastDayOfWeek()
	{
	    var date = new Date();
	    var WeekFirstDay=new Date(date-(date.getDay()-1)*86400000);
            return timeFormat(new Date((WeekFirstDay/1000+6*86400)*1000));
	}
	//获取当月第一天
	function getFirstDayOfMonth(date) 
	{
	    date.setDate(1);
	    return timeFormat(date);
	}
	//获取当月最后一天
	function getLastDayOfMonth(date)
	{
	    var currentMonth=date.getMonth();
	    var nextMonth=++currentMonth;
	    var nextMonthFirstDay=new Date(date.getFullYear(),nextMonth,1);
            var oneDay=1000*60*60*24;
	    return timeFormat(new Date(nextMonthFirstDay-oneDay));
	}
	//获得本季度的开始月份 
	function getQuarterStartMonth()
	{ 
	    var quarterStartMonth = 0; 
	    if(nowMonth<3){ 
	        quarterStartMonth = 0; 
	    } 
	    if(2<nowMonth && nowMonth<6){ 
		quarterStartMonth = 3; 
	    } 
	    if(5<nowMonth && nowMonth<9){ 
		quarterStartMonth = 6; 
	    } 
	    if(nowMonth>8){ 
		quarterStartMonth = 9; 
	    } 
	    return quarterStartMonth; 
	    }  
	//获得本季度的开端日期
        function getQuarterStartDate(){
	    var quarterStartDate = new Date(nowYear, getQuarterStartMonth(), 1);
	    return timeFormat(quarterStartDate);
        }

        //或的本季度的停止日期
        function getQuarterEndDate(){
	    var quarterEndMonth = getQuarterStartMonth() + 2;
	    var quarterStartDate = new Date(nowYear, quarterEndMonth, getMonthDays(quarterEndMonth));
	    return timeFormat(quarterStartDate);
        }
	//获得某月的天数
        function getMonthDays(myMonth){
	    var monthStartDate = new Date(nowYear, myMonth, 1);
	    var monthEndDate = new Date(nowYear, myMonth + 1, 1);
	    var days = (monthEndDate - monthStartDate)/(1000 * 60 * 60 * 24);
	    return days;
        }


java 中时间

	//当天时间
	Calendar c = Calendar.getInstance();
	c.setTime(new Date());
	String curDate = new SimpleDateFormat("yyyy-MM-dd").format(c.getTime());
	System.out.println(curDate);
	//昨天时间
	c.add(Calendar.DATE,-1);
	String preDate = new SimpleDateFormat("yyyy-MM-dd").format(c.getTime());
	System.out.println(preDate);

	//本月第一天
	c.set(Calendar.DAY_OF_MONTH, 1);
	String firstDayOfMonth = new SimpleDateFormat("yyyy-MM-dd").format(c.getTime());
	System.out.println(firstDayOfMonth);
	//本月最后一天（和第一天连在一起）
	c.roll(Calendar.DAY_OF_MONTH, -1);
	String lastDayOfMonth = new SimpleDateFormat("yyyy-MM-dd").format(c.getTime());
	System.out.println(lastDayOfMonth);

	Calendar c2 = Calendar.getInstance();
	//本周的周一
	c2.set(Calendar.DAY_OF_WEEK, 2);
	String firstDayOfWeek = new SimpleDateFormat("yyyy-MM-dd").format(c2.getTime());
	System.out.println(firstDayOfWeek);
	//本周的周天
	c2.set(Calendar.DAY_OF_WEEK, 7);
	c2.add(Calendar.DATE, 1);
	String lastDayOfWeek = new SimpleDateFormat("yyyy-MM-dd").format(c2.getTime());
	System.out.println(lastDayOfWeek);
