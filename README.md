# DOME
DOME
&lt;%@ page language=&quot;java&quot; contentType=&quot;text/html; charset=UTF-8&quot;
    pageEncoding=&quot;UTF-8&quot;%&gt;
&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD HTML 4.01 Transitional//EN&quot; &quot;http://www.w3.org/TR/html4/loose.dtd&quot;&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=UTF-8&quot;&gt;
&lt;title&gt;登入&lt;/title&gt;
   &lt;style type=&quot;text/css&quot;&gt;
    html,body{
      margin:0;
      padding:0;
      height:100%;
      border:none
   }
    &lt;/style&gt;
    &lt;script type=&quot;text/javascript&quot; src=&quot;js/jquery-1.7.1.min.js&quot;&gt;&lt;/script&gt;
&lt;script type=&quot;text/javascript&quot; src=&quot;js/jquery.form.js&quot;&gt;&lt;/script&gt;
&lt;script type=&quot;text/javascript&quot;&gt;
$(function(){
    $(document).ready(function() {
        
    
        // bind form using 'ajaxForm'
        $('#myform').ajaxForm({
            
            beforeSubmit:  function(formData, jqForm, options){
                var account = $(&quot;#account&quot;).val();
                if(account==&quot;&quot;){
                    alert(&quot;帳號不可為空白!&quot;);return false;}
                var password = $(&quot;#password&quot;).val();
                if(password==&quot;&quot;){
                    alert(&quot;密碼不可為空白!&quot;);return false;}
                
 
                $(&quot;#submit&quot;).attr(&quot;readonly&quot;,true);
            },  // pre-submit callback
            success: function(responseText, statusText, xhr, $form){
                var json = jQuery.parseJSON(responseText);
                if (json.success == false)
                {
                    alert(json.msg);
                }else
                    top.location.replace(&quot;./menus.jsp&quot;);
            },  // post-submit callback
            error:function(jqXHR, textStatus, errorThrown){
                alert(&quot;伺服器端錯誤!&quot;);
            },
            complete:function(jqXHR, textStatus)
            {
                $(&quot;#submit&quot;).attr(&quot;readonly&quot;,false);
            }
        });
    });
});
&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;table width=&quot;100%&quot; height=&quot;100%&quot;&gt;
    &lt;tr valign=&quot;middle&quot; &gt;&lt;td align=&quot;center&quot;&gt;
    &lt;form action=&quot;login.jsp&quot; method=&quot;post&quot; id=&quot;myform&quot;&gt;
        &lt;table&gt;
        &lt;tr&gt;&lt;td style=&quot;width:80px&quot;&gt;帳號&lt;/td&gt;&lt;td&gt;&lt;input id=&quot;account&quot; type=&quot;text&quot; name=&quot;account&quot; /&gt;&lt;/td&gt;&lt;/tr&gt;
        &lt;tr&gt;&lt;td style=&quot;width:80px&quot;&gt;密碼&lt;/td&gt;&lt;td&gt;&lt;input id=&quot;password&quot; type=&quot;password&quot; name=&quot;password&quot; /&gt;&lt;/td&gt;&lt;/tr&gt;
        &lt;tr&gt;&lt;td colspan=&quot;2&quot;&gt;&lt;button type=&quot;submit&quot; id=&quot;submit&quot;&gt;登入&lt;/button&gt;&lt;/td&gt;&lt;/tr&gt;
        &lt;/table&gt;
    &lt;/form&gt;
    
    &lt;/td&gt;
    &lt;/tr&gt;
    &lt;/table&gt;
&lt;/body&gt;
&lt;/html&gt;

