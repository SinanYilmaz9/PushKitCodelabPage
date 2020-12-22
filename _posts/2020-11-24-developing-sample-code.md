---
title: Create Notification Token and Topic
description: 15
---

<p><strong>1. In MainViewModel.kt file, get your APP ID. You can access your app id from  agconnect-services.json file.</strong></p>
<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    // TODO 3.0: Get your APP ID	
val appId = AGConnectServicesConfig.fromContext(getApplication()).getString("your_app_id")

<span class="pln">
</span></code></pre>
<p><strong>2. Next step, get token for push transactions. Now add this line and get your token.
</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    // TODO 3.1: Get your token
val token = HmsInstanceId.getInstance(getApplication()).getToken(appId, "HCM")
Log.i(TAG, "get token:$token")

<span class="pln">
</span></code></pre>

<p><strong>3. In MainActivity.kt file, create topic names.</strong></p>
<pre><div id="copy-button12" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>   // TODO 4.0: Choose name your topic
const val TOPIC_NAME_DAILY = "DRINK_WATER_DAILY"
const val TOPIC_NAME_WEEKLY = "DRINK_WATER_WEEKLY"

<span class="pln">
</span></code></pre>
<p><strong>4. This step, we request for topic with viewmodel.</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code> // TODO 4.1: request topic from viewmodel
if (active) {
    viewModel.subscribeTopic(topicName)
} else {
    viewModel.unSubscribeTopic(topicName)
}

 <span class="pln">
</span></code></pre>
<p><strong>5. Now, get your MainViewModel.kt file. We are sending requests to HMSMessaging under the topic name specified here. </strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code> // TODO 4.2: Request for subscribe a topic.
try {
    HmsMessaging.getInstance(getApplication()).subscribe(topic)
        .addOnCompleteListener { task ->
            if (task.isSuccessful) {
                Log.i(TAG, "Subscribe Successful!")

             when (topic) {
               MainActivity.TOPIC_NAME_DAILY -> _subscribeStatusDailyLiveData.value = true
               MainActivity.TOPIC_NAME_WEEKLY -> _subscribeStatusWeeklyLiveData.value = true
                }
            } else {
                Log.e(TAG, "Subscribe Failed: ${task.exception.message}")
            }
        }
} catch (e: Exception) {
    Log.e(TAG, "Subscribe Failed: exception= ${e.message}")


<span class="pln">
</span></code></pre>
<p><strong>6. Next step; Unsubscribe a topic. We're doing a similar procedure for unsubscribe.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  // TODO 4.3: Request for unsubscribe a topic.
try {
    HmsMessaging.getInstance(getApplication()).unsubscribe(topic)
        .addOnCompleteListener { task ->
            if (task.isSuccessful) {
                Log.i(TAG, "Unsubscribe Successful!")
 
           when (topic) {
              MainActivity.TOPIC_NAME_DAILY -> _subscribeStatusDailyLiveData.value = false
              MainActivity.TOPIC_NAME_WEEKLY ->_subscribeStatusWeeklyLiveData.value = false
                }
            } else {
                Log.e(TAG, "Unsubscribe Failed: ${task.exception.message}")
            }
        }
} catch (e: Exception) {
    Log.e(TAG, "Unsubscribe Failed: exception= ${e.message}")
}

<span class="pln">
</span></code></pre>

