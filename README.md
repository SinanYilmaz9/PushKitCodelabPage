## Topic-based Notifications with Push Kit Codelab


## Table of Contents

 * [Introduction](#introduction)
 * [Installation](#installation)
 * [Configuration ](#configuration )
 * [Supported Environments](#supported-environments)
 * [Sample Code](#Sample Code)
 * [License](#license)
 

## Introduction
    Topic-based Notifications with Push Kit Codelab encapsulates APIs of the HUAWEI Push Kit SDK. It provides many sample programs for your reference or usage.
The following describes packages of project.

    service:       The package name contains the service class of the Push Kit.
    ui:            The package name includes the activity class that the user interface is configured with.
    viewmodel:     The package name contains the viewmodel class where the network transactions are performed.
    

## Installation
    Before using Topic-based Notifications with Push Kit Codelab code, check whether the Android Studio environment has been installed. 
    Download the Topic-based Notifications with Push Kit Codelab project by zip or clone in Github.
    Wait for the gradle build in your project.

## Supported Environments
	•	Android Studio 3.x or later version
	•	Java JDK 1.8 or later version
	•	Android API Level 23 or higher version
	•	For Huawei devices running EMUI 10.0 or later, the version of HMS Core (APK) must be 3.0.0 or later. For Huawei devices running an EMUI version earlier than 10.0, the version of HMS Core (APK) must be 4.0.3 or later.

## Configuration 
    To use functions provided by packages in examples, you need to set related parameters in Topic-based Notifications with Push Kit Codelab.
    
    appId: App ID, which is obtained from app information.
    
## Sample Code
    Topic-based Notifications with Push Kit Codelab code uses the Client structure in the project.The following describes methods in the Client structure.

    1). Add your service class.
    Your service class for push notification.
    Code location src/main/java/com/hms/codelab/push/topicbased/service/PushKitCodelabService.kt
    
    2). Get your APP ID.
    You can access your appId from agconnect-services.json file.
    Code location src/main/java/com/hms/codelab/push/topicbased/viewmodel/MainViewModel.kt
    
    3). Create your token for push notification.
    Code location src/main/java/com/hms/codelab/push/topicbased/viewmodel/MainViewModel.kt
    
    4). Create your topic names.
    You can create custom topic name.
    Code location src/main/java/com/hms/codelab/push/topicbased/ui/MainActivity.kt
    
    5). Request for subscribe a topic.
    You can subsribe a topic.
    Code location src/main/java/com/hms/codelab/push/topicbased/viewmodel/MainViewModel.kt
    
    6). Request for unsubscribe a topic.
    You can unsubsribe a topic.
    Code location src/main/java/com/hms/codelab/push/topicbased/viewmodel/MainViewModel.kt


##  License
    Topic-based Notifications with Push Kit Codelab is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).
