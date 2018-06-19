---
title: 通用事件篩選模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc80168b-25bd-4228-b84c-d38bf4e2fe4a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef90a4533b8b12929488d3a323dae47976eace0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234518"
---
# <a name="common-event-filter-patterns"></a>通用事件篩選模式
以 Windows Workflow Foundation (WF) 的 BAM 攔截器進行工作時，您很可能會注意到，自己在攔截器組態檔中經常是使用一組通用篩選模式。 雖然其中有些是您的應用程式和環境專屬的篩選模式，但多數模式是可以跨多種環境並可用於多種應用程式中。  
  
 本主題收集了許多針對 WF 應用程式撰寫，由攔截器組態檔所使用的通用篩選模式。 這些模式會根據 Windows Workflow Foundation 追蹤事件分組：  
  
-   活動狀態事件  
  
-   工作流程狀態事件  
  
-   使用者事件  
  
 每個模式都可以複製到您的攔截器組態檔中，並可修改成適合您的應用程式。  
  
## <a name="activity-status-event-filter-patterns"></a>活動狀態事件篩選模式  
 活動是工作流程的基礎建置區塊。 工作流程就是以階層方式組織在樹狀結構中的一組活動。 活動則代表工作流程中的一項動作。 它可以是像是「延遲」的簡單動作，或是由多個子活動所組成的複合活動。  
  
 本節中的篩選條件來篩選活動和 WF 自訂作業使用一或多個下列的 BAM 攔截器：  
  
-   GetActivityName  
  
-   GetActivityEvent  
  
-   GetActivityType  
  
-   GetActivityProperty  
  
-   GetWorkflowProperty  
  
-   GetContextProperty  
  
> [!NOTE]
>  如果篩選中沒有使用 GetActivityEvent 作業，您的篩選將只尋找「結案」活動事件。  
  
### <a name="filter-by-activity-name-closed-activity"></a>依活動名稱篩選 (結案活動)  
 您將經常需要依據活動名稱來篩選結案活動事件。 當您需要從特定活動 (例如接收檔案或是將資料寫入至資料庫) 擷取資料時，就可以使用這種篩選。  
  
 下列程式碼片段會篩選出名為 "MyActivity" 的結案活動。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-closed-activity-event"></a>依活動型別篩選 (結案活動事件)  
 有時候您需要依據型別 (而非名稱) 來篩選活動。 例如，您可能要針對工作流程中的所有活動儲存活動名稱及日期/時間戳記。 若要達成此目的，您使用`GetActivityType`作業。 `GetActivityType`比較提供的型別與基底型別及所有衍生型別，以判斷相符。 與 `System.Workflow.ComponentModel.Activity` 的比較結果一定是相符，因為所有的工作流程活動都是從此型別所衍生。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-event-any-activity-type"></a>依活動事件篩選 (任何活動型別)  
 這個篩選會使用 GetActivityEvent 作業來尋找結案活動。 這樣有助於擷取所有結案活動 (而非依據名稱或型別之特定事件) 的相關資訊。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-type-closed-activity-event"></a>依活動名稱和型別篩選 (結案活動事件)  
 如果要指定有興趣尋找之活動的確實型別 (包括處理器架構)，您可以依活動名稱和活動型別來選擇篩選活動。 下面範例會尋找從 `System.Workflow.ComponentModel.Activity` 衍生的 "MyActivity"，而您可以將這個型別變更為其他的衍生型別，提高篩選的限制性。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
<ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-event-any-activity-type"></a>依活動名稱和型別篩選 (結案活動事件)  
 這個運算式會依活動名稱和活動事件進行篩選。 當您要擷取特定活動和事件的資訊，或是要從指定之活動的一個以上活動事件擷取資料時，就可以使用這種篩選。 例如，您可能需要針對 MyActivity 使用兩個不同的 OnEvent 項目，一個用於「執行中」，另一個用於「結案」，如下所示。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-event"></a>依活動型別和事件篩選  
 在單一活動事件期間擷取衍生自特定型別之所有活動的資訊時，就可以使用這種篩選。 例如，您可能想要在某筆訂單流經工作流程時，追蹤其訂單 ID 及日期/時間戳記。 若要達成此目的，您使用`GetActivityEvent`和`GetActivityType`作業。 `GetActivityType`比較提供的型別與基底型別及所有衍生型別，以判斷相符。 與 `System.Workflow.ComponentModel.Activity` 的比較結果一定是相符，因為所有的工作流程活動都是從此型別所衍生。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-type-and-event"></a>依活動名稱、型別及事件篩選  
 若要更進一步地限定您有興趣追蹤的活動時，就可以使用這種依名稱、型別及事件的篩選。 例如，下面這個篩選會尋找型別為 `System.Workflow.ComponentModel.Activity`，或是自其中衍生型別的結案活動 "MyActivity"。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="workflow-status-event-filter-patterns"></a>工作流程狀態事件篩選模式  
 本節中的篩選會篩選工作流程事件，並使用下列一或多個適用於 WF 自訂作業的 BAM 攔截器：  
  
-   GetWorkflowEvent  
  
-   GetContextProperty  
  
### <a name="filter-by-workflow-event"></a>依工作流程事件篩選  
 這個運算式會依工作流程事件篩選。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Created</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="user-event-filter-patterns"></a>使用者事件篩選模式  
 如果應用程式會使用 TrackData 方法追蹤自訂資訊，您便可以使用下列一或多個 WF 自訂使用者資料作業的 BAM 攔截器，根據資料的特性來進行篩選：  
  
-   GetUserDataType  
  
-   GetUserKey  
  
-   GetUserData  
  
 這個篩選可以透過下列作業來合併這些自訂作業，以建立更複雜的運算式：  
  
-   GetActivityName  
  
-   GetActivityType  
  
-   GetActivityProperty  
  
-   GetWorkflowProperty  
  
-   GetContextProperty  
  
 如果您的篩選中連一個使用者資料作業都沒有，您的篩選就不會是使用者事件篩選，而且封入的 OnEvent 將會造成錯誤 (如果使用者作業出現在對應的更新運算式中)，或是會被識別為活動追蹤點，而非使用者追蹤點。  
  
### <a name="filter-by-activity-name-and-user-data-type"></a>依活動名稱和使用者資料型別篩選  
 大多數時候，您都可以根據活動名稱和使用者資料型別來識別事件。 下列運算式會篩選出名為 "MyActivity" 的活動，以及衍生自 `System.Object` 的使用者資料型別。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-user-data-type"></a>依活動型別和使用者資料型別篩選  
 您可以根據活動型別和使用者資料型別來篩選。 這個篩選可以讓您根據型別和從其中衍生型別來進行篩選，因為 `GetActivityType` 和 `GetUserDataType` 兩者都會就所指定的型別和所有衍生型別進行比較。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-and-user-data-type"></a>依活動名稱、活動型別及使用者資料型別篩選  
 這種篩選會透過包含活動名稱，更進一步地限制活動型別和使用者資料型別篩選模式。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-user-key"></a>依活動名稱和使用者金鑰篩選  
 如果應用程式包含會配合在執行階段所決定的金鑰來呼叫 `TrackData` 的活動，您可能就會想要依據活動名稱和使用者金鑰來進行篩選。 這種篩選可讓您根據特定金鑰值來觸發 `OnEvent`。 例如，您的應用程式可能會定義多個金鑰，而在某個活動內動態地選取其中一個金鑰。  
  
 下面這個運算式會篩選出包含名為 "ItemKey" 之使用者金鑰的 "MyActivity"。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-user-key"></a>依活動型別和使用者金鑰篩選  
 如果您的應用程式包含多個會配合在執行階段決定的金鑰呼叫 `TrackData` 的活動，您可能就會想要依據活動名稱和使用者金鑰來進行篩選。 這種篩選可讓您根據特定金鑰值來觸發 `OnEvent`。 例如，您的應用程式可能會定義多個金鑰，而在某個活動內動態地選取其中一個金鑰。  
  
 下面這個運算式會篩選出衍生自 `System.Workflow.ComponentModel.Activity` 並包含名為 "ItemKey" 之使用者金鑰的所有活動。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-and-user-key"></a>依活動名稱、活動型別及使用者金鑰篩選  
 這種篩選模式會透過在篩選中包含活動名稱，更進一步地精簡活動型別和使用者金鑰篩選模式。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-user-data-type-and-user-key"></a>依活動名稱、活動型別、使用者資料型別及使用者金鑰篩選  
 當您要將篩選限制成具有特定使用者金鑰和衍生自特定資料型別的具名活動，就可以使用這種篩選。 例如，您的活動可能會配合金鑰 "Item" 以及字串或整數的資料值 (依項目型別來決定)，來呼叫 TrackData。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-user-data-type-and-user-key"></a>依活動型別、使用者資料型別及使用者金鑰篩選  
 當您要將篩選限制成具有特定使用者金鑰且從特定資料型別衍生的活動型別，就可以使用這種篩選。 相較起根據所使用型別而使用活動名稱、使用者資料型別和使用者金鑰，這種篩選的限制性可能會更高或是更低。 如果是指定最具衍生性的型別，篩選的限制性會更高，但如果是指定根基底型別，篩選的限制性就會比較低。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-user-data-type-and-user-key"></a>依活動名稱、活動型別、使用者資料型別及使用者金鑰篩選  
 這種篩選會透過加入活動名稱，更進一步地限制活動型別、使用者資料型別及使用者金鑰模式。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>   
```