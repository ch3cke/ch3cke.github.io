---
title: hot
date: 2021-10-21 19:04:31
comments: false
---
<div id="hot"></div>
<script src="/js/av-core-mini-0.6.4.js"></script>
<script>AV.initialize("jXRYdAHIc85p63qqPqoov6rQ-MdYXbMMI", "1JUgviDin9HY4U3bG0KOmBL2");</script>
<script type="text/javascript">
  var time=0;
  var count=0;
  var title="";
  var url="";
  var query = new AV.Query('Counter');
  query.notEqualTo('id',0);
  query.descending('time');
  query.limit(1000);
  query.find().then(function (todo) {
    for (var i=0;i<1000;i++){
      count++;
      //修改下方10，调整排行显示的条数
      if(count > 10){
        break; 
      }
      var result=todo[i].attributes;
      //下方的30可以根据网站访问量调整，以控制最大热度的数值
      time=parseInt((result.time)/30);
      title=result.title;
      url=result.url;
      //下方域名修改为自己的网站
      var content="<p>"+"<font color='#1C1C1C'>"+"【文章热度:"+time+"℃】"+"</font>"+"<a href='"+"https://ch3cke.github.io"+url+"'>"+title+"</a>"+"</p>";
      document.getElementById("hot").innerHTML+=content
    }
  }, function (error) {
    console.log("error");
  });
</script>