---
title: lua GBK编码数组转换成字符串
date: 2023-04-04 08:18:01
tags: lua
---

# lua GBK编码数组转换成字符串

{% codeblock [title] [lang:language] [url] [link text] [additional options] %}
---字节数组转字符串
function arrayToString(array)
 local strMiddle= ''
 for i=1,#array do
  strMiddle=strMiddle..string.char(array[i])  
 end  
 return strMiddle; 
end 
{% endcodeblock %}