---
title: Topic Management on the Server
description: 5
---

<ol type="1">
<li><h3>Subscribe / Unsubcribe a topic</h3></li>
  <p>The Push Kit server provides basic APIs for topic management. A maximum of 1,000 tokens can be passed for subscribing to or unsubscribing from a topic at a time. Each app has a maximum of 2,000 different topics.</p>
  
<pre><div id="copy-button33" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  https://push-api.cloud.huawei.com/v1/[yourAppId]/topic:subscribe 
<span class="pln">
</span></code></pre>
<p>You need to post the request to the address above. If you want to unsubscribe, just change the word at the end of the URL. You should send the information below in the header.</p>
<br><img style="width: 400.00px" src="https://raw.githubusercontent.com/SinanYilmaz9/PushKitCodelabPage/main/assets/manifestService.png" onclick="imageclick(src)">

<p>And your request message body;</p>
<pre><div id="copy-button34" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  { "topic": "DRINK_WATER_DAILY",
"tokenArray": [ 
"AOffIB70WGIqdFJWJvwG7SOB...xRVgtbqhESkoJLlW-TKeTjQvzeLm8Up1-3K7" 
] 
}
<span class="pln">
</span></code></pre>

 <li><h3>Send Messages by Topic</h3></li>
<p>After subscribing to a topic, you must post a request to the URL below to send a notification to the topic.</strong></p>
<pre><div id="copy-button35" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  https://push-api.cloud.huawei.com/v1/[yourAppId]/messages:send
<span class="pln">
</span></code></pre>
<p>We have the same header parameters.</p>
<br><img style="width: 400.00px" src="https://raw.githubusercontent.com/SinanYilmaz9/PushKitCodelabPage/main/assets/manifestService.png" onclick="imageclick(src)">
<p>Sample code for request body</p>
<pre><div id="copy-button36" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  { "validate_only": false, 
"message": { 
	"notification": { 
		"title": "WATER TIME", 
		"body": "Please drink water!" }, 
	"android": { 
		"notification": { 
	"click_action": { 
		"type": 1, 
		"action": "com.dtse.pushcodelab.intent.action.test" 
} 
	} 
}, 
	"topic": "DRINK_WATER_DAILY"
 }
 }

<span class="pln">
</span></code></pre>

 <li><h3>Message Sending by Conditions</h3></li>
 <p>In addition, Push Kit allows you to send messages by topic combinations specified by condition.
This function enables you to send topic-based messages based on a combination of conditions, or in another word, a Boolean expression of target topics. For example, you can send messages to users who have subscribed to both the DRINK_WATER_DAILY and DRINK_WATER_WEEKLY topics.

All we have to do is use condition key in request body when sending the notification.</p>
<pre><div id="copy-button37" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  
{ "validate_only": false, 
"message": { 
	"notification": { 
		"title": "WATER TIME", 
		"body": "Please drink water!" }, 
	"android": { 
		"notification": { 
	"click_action": { 
		"type": 1, 
		"action": "com.dtse.pushcodelab.intent.action.test" 
} 
	} 
}, 
	"condition": "’DRINK_WATER_DAILY’ in topics && ‘DRINK_WATER_WEEKLY’ in topics"
 }
 }
<span class="pln">
</span></code></pre>
<p>After sending the notification request, it must have been on the notification device.</p>
<br><img style="width: 400.00px" src="https://raw.githubusercontent.com/SinanYilmaz9/PushKitCodelabPage/main/assets/notifFromServer.png" onclick="imageclick(src)">
</ol>
