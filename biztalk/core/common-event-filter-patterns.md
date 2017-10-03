---
title: "通用事件篩選模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc80168b-25bd-4228-b84c-d38bf4e2fe4a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef90a4533b8b12929488d3a323dae47976eace0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="common-event-filter-patterns"></a><span data-ttu-id="a074d-102">通用事件篩選模式</span><span class="sxs-lookup"><span data-stu-id="a074d-102">Common Event Filter Patterns</span></span>
<span data-ttu-id="a074d-103">以 Windows Workflow Foundation (WF) 的 BAM 攔截器進行工作時，您很可能會注意到，自己在攔截器組態檔中經常是使用一組通用篩選模式。</span><span class="sxs-lookup"><span data-stu-id="a074d-103">As you work with the BAM Interceptor for Windows Workflow Foundation (WF), you will likely notice that there are a set of common filter patterns that you will use frequently in your interceptor configuration files.</span></span> <span data-ttu-id="a074d-104">雖然其中有些是您的應用程式和環境專屬的篩選模式，但多數模式是可以跨多種環境並可用於多種應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a074d-104">While some of these filter patterns will be unique to your applications and environments, many patterns can be used across environments and in diverse applications.</span></span>  
  
 <span data-ttu-id="a074d-105">本主題收集了許多針對 WF 應用程式撰寫，由攔截器組態檔所使用的通用篩選模式。</span><span class="sxs-lookup"><span data-stu-id="a074d-105">This topic collects many of the common filter patterns used by interceptor configuration files written for WF applications.</span></span> <span data-ttu-id="a074d-106">這些模式會根據 Windows Workflow Foundation 追蹤事件分組：</span><span class="sxs-lookup"><span data-stu-id="a074d-106">Patterns are grouped by Windows Workflow Foundation tracking event:</span></span>  
  
-   <span data-ttu-id="a074d-107">活動狀態事件</span><span class="sxs-lookup"><span data-stu-id="a074d-107">Activity status events</span></span>  
  
-   <span data-ttu-id="a074d-108">工作流程狀態事件</span><span class="sxs-lookup"><span data-stu-id="a074d-108">Workflow status events</span></span>  
  
-   <span data-ttu-id="a074d-109">使用者事件</span><span class="sxs-lookup"><span data-stu-id="a074d-109">User events</span></span>  
  
 <span data-ttu-id="a074d-110">每個模式都可以複製到您的攔截器組態檔中，並可修改成適合您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a074d-110">Each pattern can be copied into your interceptor configuration file and modified to suit your application.</span></span>  
  
## <a name="activity-status-event-filter-patterns"></a><span data-ttu-id="a074d-111">活動狀態事件篩選模式</span><span class="sxs-lookup"><span data-stu-id="a074d-111">Activity Status Event Filter Patterns</span></span>  
 <span data-ttu-id="a074d-112">活動是工作流程的基礎建置區塊。</span><span class="sxs-lookup"><span data-stu-id="a074d-112">Activities are the fundamental building blocks of workflows.</span></span> <span data-ttu-id="a074d-113">工作流程就是以階層方式組織在樹狀結構中的一組活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-113">A workflow is a set of activities that are organized hierarchically in a tree structure.</span></span> <span data-ttu-id="a074d-114">活動則代表工作流程中的一項動作。</span><span class="sxs-lookup"><span data-stu-id="a074d-114">An activity represents an action in a workflow.</span></span> <span data-ttu-id="a074d-115">它可以是像是「延遲」的簡單動作，或是由多個子活動所組成的複合活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-115">It can be a simple action such as a delay, or it can be a composite activity that consists of several child activities.</span></span>  
  
 <span data-ttu-id="a074d-116">本節中的篩選條件來篩選活動和 WF 自訂作業使用一或多個下列的 BAM 攔截器：</span><span class="sxs-lookup"><span data-stu-id="a074d-116">The filters in this section filter activities and use one or more of the following BAM Interceptor for WF custom operations:</span></span>  
  
-   <span data-ttu-id="a074d-117">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="a074d-117">GetActivityName</span></span>  
  
-   <span data-ttu-id="a074d-118">GetActivityEvent</span><span class="sxs-lookup"><span data-stu-id="a074d-118">GetActivityEvent</span></span>  
  
-   <span data-ttu-id="a074d-119">GetActivityType</span><span class="sxs-lookup"><span data-stu-id="a074d-119">GetActivityType</span></span>  
  
-   <span data-ttu-id="a074d-120">GetActivityProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-120">GetActivityProperty</span></span>  
  
-   <span data-ttu-id="a074d-121">GetWorkflowProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-121">GetWorkflowProperty</span></span>  
  
-   <span data-ttu-id="a074d-122">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-122">GetContextProperty</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a074d-123">如果篩選中沒有使用 GetActivityEvent 作業，您的篩選將只尋找「結案」活動事件。</span><span class="sxs-lookup"><span data-stu-id="a074d-123">If you do not use the GetActivityEvent operation in your filter, your filter will look for Closed activity events only.</span></span>  
  
### <a name="filter-by-activity-name-closed-activity"></a><span data-ttu-id="a074d-124">依活動名稱篩選 (結案活動)</span><span class="sxs-lookup"><span data-stu-id="a074d-124">Filter by Activity Name (Closed Activity)</span></span>  
 <span data-ttu-id="a074d-125">您將經常需要依據活動名稱來篩選結案活動事件。</span><span class="sxs-lookup"><span data-stu-id="a074d-125">You will frequently need to filter for closed activity events by activity name.</span></span> <span data-ttu-id="a074d-126">當您需要從特定活動 (例如接收檔案或是將資料寫入至資料庫) 擷取資料時，就可以使用這種篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-126">This is useful when you need to capture data from a specific activity such as receiving a file or writing data to a database.</span></span>  
  
 <span data-ttu-id="a074d-127">下列程式碼片段會篩選出名為 "MyActivity" 的結案活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-127">The fragment below filters for a closed activity named "MyActivity".</span></span>  
  
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
  
### <a name="filter-by-activity-type-closed-activity-event"></a><span data-ttu-id="a074d-128">依活動型別篩選 (結案活動事件)</span><span class="sxs-lookup"><span data-stu-id="a074d-128">Filter by Activity Type (Closed Activity Event)</span></span>  
 <span data-ttu-id="a074d-129">有時候您需要依據型別 (而非名稱) 來篩選活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-129">There will be times when you want to filter an activity by type rather than name.</span></span> <span data-ttu-id="a074d-130">例如，您可能要針對工作流程中的所有活動儲存活動名稱及日期/時間戳記。</span><span class="sxs-lookup"><span data-stu-id="a074d-130">For example, you may want to save activity name and a date/time stamp for all activities in a workflow.</span></span> <span data-ttu-id="a074d-131">若要達成此目的，您使用`GetActivityType`作業。</span><span class="sxs-lookup"><span data-stu-id="a074d-131">To accomplish this, you use the `GetActivityType` operation.</span></span> <span data-ttu-id="a074d-132">`GetActivityType`比較提供的型別與基底型別及所有衍生型別，以判斷相符。</span><span class="sxs-lookup"><span data-stu-id="a074d-132">`GetActivityType` compares a supplied type against the base type and all derived types to determine a match.</span></span> <span data-ttu-id="a074d-133">與 `System.Workflow.ComponentModel.Activity` 的比較結果一定是相符，因為所有的工作流程活動都是從此型別所衍生。</span><span class="sxs-lookup"><span data-stu-id="a074d-133">Comparing against `System.Workflow.ComponentModel.Activity` will match since all workflow activities must derive from it.</span></span>  
  
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
  
### <a name="filter-by-activity-event-any-activity-type"></a><span data-ttu-id="a074d-134">依活動事件篩選 (任何活動型別)</span><span class="sxs-lookup"><span data-stu-id="a074d-134">Filter by Activity Event (Any Activity Type)</span></span>  
 <span data-ttu-id="a074d-135">這個篩選會使用 GetActivityEvent 作業來尋找結案活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-135">This filter uses the GetActivityEvent operation to find closed activities.</span></span> <span data-ttu-id="a074d-136">這樣有助於擷取所有結案活動 (而非依據名稱或型別之特定事件) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a074d-136">It is useful for capturing information about all closed events (versus a specific event by name or type).</span></span>  
  
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
  
### <a name="filter-by-activity-name-and-type-closed-activity-event"></a><span data-ttu-id="a074d-137">依活動名稱和型別篩選 (結案活動事件)</span><span class="sxs-lookup"><span data-stu-id="a074d-137">Filter by Activity Name and Type (Closed Activity Event)</span></span>  
 <span data-ttu-id="a074d-138">如果要指定有興趣尋找之活動的確實型別 (包括處理器架構)，您可以依活動名稱和活動型別來選擇篩選活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-138">You may choose to filter activities by activity name and activity type if you want to specify the exact type of activity (including processor architecture) that you are interested in finding.</span></span> <span data-ttu-id="a074d-139">下面範例會尋找從 `System.Workflow.ComponentModel.Activity` 衍生的 "MyActivity"，而您可以將這個型別變更為其他的衍生型別，提高篩選的限制性。</span><span class="sxs-lookup"><span data-stu-id="a074d-139">The sample below looks for "MyActivity" deriving from `System.Workflow.ComponentModel.Activity`; you can change this to a derived type to make it more restrictive.</span></span>  
  
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
  
### <a name="filter-by-activity-name-and-event-any-activity-type"></a><span data-ttu-id="a074d-140">依活動名稱和型別篩選 (結案活動事件)</span><span class="sxs-lookup"><span data-stu-id="a074d-140">Filter by Activity Name and Event (Any Activity Type)</span></span>  
 <span data-ttu-id="a074d-141">這個運算式會依活動名稱和活動事件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-141">This expression filters based on activity name and activity event.</span></span> <span data-ttu-id="a074d-142">當您要擷取特定活動和事件的資訊，或是要從指定之活動的一個以上活動事件擷取資料時，就可以使用這種篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-142">This is useful when you want to capture information for a specific activity and event or when capturing data from more than one activity event for a given activity.</span></span> <span data-ttu-id="a074d-143">例如，您可能需要針對 MyActivity 使用兩個不同的 OnEvent 項目，一個用於「執行中」，另一個用於「結案」，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a074d-143">For example, you may want two different OnEvent elements, one for MyActivity when it is Executing and one for when it is Closed as shown below.</span></span>  
  
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
  
### <a name="filter-by-activity-type-and-event"></a><span data-ttu-id="a074d-144">依活動型別和事件篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-144">Filter by Activity Type and Event</span></span>  
 <span data-ttu-id="a074d-145">在單一活動事件期間擷取衍生自特定型別之所有活動的資訊時，就可以使用這種篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-145">This filter is useful for capturing information about all activities that derive from a specific type during a single activity event.</span></span> <span data-ttu-id="a074d-146">例如，您可能想要在某筆訂單流經工作流程時，追蹤其訂單 ID 及日期/時間戳記。</span><span class="sxs-lookup"><span data-stu-id="a074d-146">For example, you may be interested in tracking a purchase order ID and date/time stamp from a purchase order as it flows through a workflow.</span></span> <span data-ttu-id="a074d-147">若要達成此目的，您使用`GetActivityEvent`和`GetActivityType`作業。</span><span class="sxs-lookup"><span data-stu-id="a074d-147">To accomplish this, you use the `GetActivityEvent` and the `GetActivityType` operations.</span></span> <span data-ttu-id="a074d-148">`GetActivityType`比較提供的型別與基底型別及所有衍生型別，以判斷相符。</span><span class="sxs-lookup"><span data-stu-id="a074d-148">`GetActivityType` compares a supplied type against the base type and all derived types to determine a match.</span></span> <span data-ttu-id="a074d-149">與 `System.Workflow.ComponentModel.Activity` 的比較結果一定是相符，因為所有的工作流程活動都是從此型別所衍生。</span><span class="sxs-lookup"><span data-stu-id="a074d-149">Comparing against `System.Workflow.ComponentModel.Activity` will match since all workflow activities must derive from it.</span></span>  
  
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
  
### <a name="filter-by-activity-name-type-and-event"></a><span data-ttu-id="a074d-150">依活動名稱、型別及事件篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-150">Filter by Activity Name, Type, and Event</span></span>  
 <span data-ttu-id="a074d-151">若要更進一步地限定您有興趣追蹤的活動時，就可以使用這種依名稱、型別及事件的篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-151">Filtering an activity by name, type and event can be useful when you want to better qualify the activity you are interested in tracking.</span></span> <span data-ttu-id="a074d-152">例如，下面這個篩選會尋找型別為 `System.Workflow.ComponentModel.Activity`，或是自其中衍生型別的結案活動 "MyActivity"。</span><span class="sxs-lookup"><span data-stu-id="a074d-152">For example, the filter below looks for the closed activity "MyActivity" that has a type that is equal to or derives from `System.Workflow.ComponentModel.Activity`.</span></span>  
  
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
  
## <a name="workflow-status-event-filter-patterns"></a><span data-ttu-id="a074d-153">工作流程狀態事件篩選模式</span><span class="sxs-lookup"><span data-stu-id="a074d-153">Workflow Status Event Filter Patterns</span></span>  
 <span data-ttu-id="a074d-154">本節中的篩選會篩選工作流程事件，並使用下列一或多個適用於 WF 自訂作業的 BAM 攔截器：</span><span class="sxs-lookup"><span data-stu-id="a074d-154">The filters in this section filter workflow events and use one or more of the following BAM Interceptor for WF custom operations:</span></span>  
  
-   <span data-ttu-id="a074d-155">GetWorkflowEvent</span><span class="sxs-lookup"><span data-stu-id="a074d-155">GetWorkflowEvent</span></span>  
  
-   <span data-ttu-id="a074d-156">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-156">GetContextProperty</span></span>  
  
### <a name="filter-by-workflow-event"></a><span data-ttu-id="a074d-157">依工作流程事件篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-157">Filter by Workflow Event</span></span>  
 <span data-ttu-id="a074d-158">這個運算式會依工作流程事件篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-158">This expression filters by workflow event.</span></span>  
  
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
  
## <a name="user-event-filter-patterns"></a><span data-ttu-id="a074d-159">使用者事件篩選模式</span><span class="sxs-lookup"><span data-stu-id="a074d-159">User Event Filter Patterns</span></span>  
 <span data-ttu-id="a074d-160">如果應用程式會使用 TrackData 方法追蹤自訂資訊，您便可以使用下列一或多個 WF 自訂使用者資料作業的 BAM 攔截器，根據資料的特性來進行篩選：</span><span class="sxs-lookup"><span data-stu-id="a074d-160">If your application tracks custom information using the TrackData method, you can filter based on the characteristics of the data using one or more of the following BAM Interceptor for WF custom user data operations:</span></span>  
  
-   <span data-ttu-id="a074d-161">GetUserDataType</span><span class="sxs-lookup"><span data-stu-id="a074d-161">GetUserDataType</span></span>  
  
-   <span data-ttu-id="a074d-162">GetUserKey</span><span class="sxs-lookup"><span data-stu-id="a074d-162">GetUserKey</span></span>  
  
-   <span data-ttu-id="a074d-163">GetUserData</span><span class="sxs-lookup"><span data-stu-id="a074d-163">GetUserData</span></span>  
  
 <span data-ttu-id="a074d-164">這個篩選可以透過下列作業來合併這些自訂作業，以建立更複雜的運算式：</span><span class="sxs-lookup"><span data-stu-id="a074d-164">The filter can combine these operations with the following to create a more complex expression:</span></span>  
  
-   <span data-ttu-id="a074d-165">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="a074d-165">GetActivityName</span></span>  
  
-   <span data-ttu-id="a074d-166">GetActivityType</span><span class="sxs-lookup"><span data-stu-id="a074d-166">GetActivityType</span></span>  
  
-   <span data-ttu-id="a074d-167">GetActivityProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-167">GetActivityProperty</span></span>  
  
-   <span data-ttu-id="a074d-168">GetWorkflowProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-168">GetWorkflowProperty</span></span>  
  
-   <span data-ttu-id="a074d-169">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="a074d-169">GetContextProperty</span></span>  
  
 <span data-ttu-id="a074d-170">如果您的篩選中連一個使用者資料作業都沒有，您的篩選就不會是使用者事件篩選，而且封入的 OnEvent 將會造成錯誤 (如果使用者作業出現在對應的更新運算式中)，或是會被識別為活動追蹤點，而非使用者追蹤點。</span><span class="sxs-lookup"><span data-stu-id="a074d-170">If your filter does not include at least one user data operation, your filter will not be a user event filter and the enclosing OnEvent will cause an error (if a user operation appears in a corresponding update expression) or will be identified as an activity track point and not a user track point.</span></span>  
  
### <a name="filter-by-activity-name-and-user-data-type"></a><span data-ttu-id="a074d-171">依活動名稱和使用者資料型別篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-171">Filter by Activity Name and User Data Type</span></span>  
 <span data-ttu-id="a074d-172">大多數時候，您都可以根據活動名稱和使用者資料型別來識別事件。</span><span class="sxs-lookup"><span data-stu-id="a074d-172">Frequently you can identify an event by activity name and user data type.</span></span> <span data-ttu-id="a074d-173">下列運算式會篩選出名為 "MyActivity" 的活動，以及衍生自 `System.Object` 的使用者資料型別。</span><span class="sxs-lookup"><span data-stu-id="a074d-173">The following expression filters for an activity named "MyActivity" and a user data type that derives from `System.Object`.</span></span>  
  
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
  
### <a name="filter-by-activity-type-and-user-data-type"></a><span data-ttu-id="a074d-174">依活動型別和使用者資料型別篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-174">Filter by Activity Type and User Data Type</span></span>  
 <span data-ttu-id="a074d-175">您可以根據活動型別和使用者資料型別來篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-175">You can filter based on activity type and user data type.</span></span> <span data-ttu-id="a074d-176">這個篩選可以讓您根據型別和從其中衍生型別來進行篩選，因為 `GetActivityType` 和 `GetUserDataType` 兩者都會就所指定的型別和所有衍生型別進行比較。</span><span class="sxs-lookup"><span data-stu-id="a074d-176">This grants you the latitude to filter events based on the type the derive from because both `GetActivityType` and `GetUserDataType` compare against the type specified and all derived types.</span></span>  
  
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
  
### <a name="filter-by-activity-name-activity-type-and-user-data-type"></a><span data-ttu-id="a074d-177">依活動名稱、活動型別及使用者資料型別篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-177">Filter by Activity Name, Activity Type, and User Data Type</span></span>  
 <span data-ttu-id="a074d-178">這種篩選會透過包含活動名稱，更進一步地限制活動型別和使用者資料型別篩選模式。</span><span class="sxs-lookup"><span data-stu-id="a074d-178">This filter further restricts the activity type and user data type filter pattern by including activity name.</span></span>  
  
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
  
### <a name="filter-by-activity-name-and-user-key"></a><span data-ttu-id="a074d-179">依活動名稱和使用者金鑰篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-179">Filter by Activity Name and User Key</span></span>  
 <span data-ttu-id="a074d-180">如果應用程式包含會配合在執行階段所決定的金鑰來呼叫 `TrackData` 的活動，您可能就會想要依據活動名稱和使用者金鑰來進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-180">If your application has an activity that calls `TrackData` with a key determined at run time, you may want to filter by activity name and user key.</span></span> <span data-ttu-id="a074d-181">這種篩選可讓您根據特定金鑰值來觸發 `OnEvent`。</span><span class="sxs-lookup"><span data-stu-id="a074d-181">This will enable you to trigger an `OnEvent` based on a specific key value.</span></span> <span data-ttu-id="a074d-182">例如，您的應用程式可能會定義多個金鑰，而在某個活動內動態地選取其中一個金鑰。</span><span class="sxs-lookup"><span data-stu-id="a074d-182">For example, your application might define multiple keys and dynamically select one within an activity.</span></span>  
  
 <span data-ttu-id="a074d-183">下面這個運算式會篩選出包含名為 "ItemKey" 之使用者金鑰的 "MyActivity"。</span><span class="sxs-lookup"><span data-stu-id="a074d-183">The expression below filters for "MyActivity" containing a user key named "ItemKey".</span></span>  
  
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
  
### <a name="filter-by-activity-type-and-user-key"></a><span data-ttu-id="a074d-184">依活動型別和使用者金鑰篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-184">Filter by Activity Type and User Key</span></span>  
 <span data-ttu-id="a074d-185">如果您的應用程式包含多個會配合在執行階段決定的金鑰呼叫 `TrackData` 的活動，您可能就會想要依據活動名稱和使用者金鑰來進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-185">If your application contain multiple activities that call `TrackData` with a key determined at run time, you may want to filter by activity name and user key.</span></span> <span data-ttu-id="a074d-186">這種篩選可讓您根據特定金鑰值來觸發 `OnEvent`。</span><span class="sxs-lookup"><span data-stu-id="a074d-186">This will enable you to trigger an `OnEvent` based on a specific key value.</span></span> <span data-ttu-id="a074d-187">例如，您的應用程式可能會定義多個金鑰，而在某個活動內動態地選取其中一個金鑰。</span><span class="sxs-lookup"><span data-stu-id="a074d-187">For example, your application might define multiple keys and dynamically select one within an activity.</span></span>  
  
 <span data-ttu-id="a074d-188">下面這個運算式會篩選出衍生自 `System.Workflow.ComponentModel.Activity` 並包含名為 "ItemKey" 之使用者金鑰的所有活動。</span><span class="sxs-lookup"><span data-stu-id="a074d-188">The expression below filters for any activity deriving from `System.Workflow.ComponentModel.Activity` containing a user key named "ItemKey".</span></span>  
  
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
  
### <a name="filter-by-activity-name-activity-type-and-user-key"></a><span data-ttu-id="a074d-189">依活動名稱、活動型別及使用者金鑰篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-189">Filter by Activity Name, Activity Type, and User Key</span></span>  
 <span data-ttu-id="a074d-190">這種篩選模式會透過在篩選中包含活動名稱，更進一步地精簡活動型別和使用者金鑰篩選模式。</span><span class="sxs-lookup"><span data-stu-id="a074d-190">This filter pattern further refines the activity type and user key filter pattern by including the activity name in the filter.</span></span>  
  
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
  
### <a name="filter-by-activity-name-user-data-type-and-user-key"></a><span data-ttu-id="a074d-191">依活動名稱、活動型別、使用者資料型別及使用者金鑰篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-191">Filter by Activity Name, User Data Type, and User Key</span></span>  
 <span data-ttu-id="a074d-192">當您要將篩選限制成具有特定使用者金鑰和衍生自特定資料型別的具名活動，就可以使用這種篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-192">This filter is useful when you want to restrict your filter to a named activity with a specific user key and deriving from a specific data type.</span></span> <span data-ttu-id="a074d-193">例如，您的活動可能會配合金鑰 "Item" 以及字串或整數的資料值 (依項目型別來決定)，來呼叫 TrackData。</span><span class="sxs-lookup"><span data-stu-id="a074d-193">For example, your activity may call TrackData using the key "Item" and a data value of string or integer depending upon the item type.</span></span>  
  
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
  
### <a name="filter-by-activity-type-user-data-type-and-user-key"></a><span data-ttu-id="a074d-194">依活動型別、使用者資料型別及使用者金鑰篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-194">Filter by Activity Type, User Data Type, and User Key</span></span>  
 <span data-ttu-id="a074d-195">當您要將篩選限制成具有特定使用者金鑰且從特定資料型別衍生的活動型別，就可以使用這種篩選。</span><span class="sxs-lookup"><span data-stu-id="a074d-195">This filter is useful when you want to restrict your filter to an activity type with a specific user key and deriving from a specific data type.</span></span> <span data-ttu-id="a074d-196">相較起根據所使用型別而使用活動名稱、使用者資料型別和使用者金鑰，這種篩選的限制性可能會更高或是更低。</span><span class="sxs-lookup"><span data-stu-id="a074d-196">It can be more restrictive or less restrictive than using activity name, user data type, and user key based on the type used.</span></span> <span data-ttu-id="a074d-197">如果是指定最具衍生性的型別，篩選的限制性會更高，但如果是指定根基底型別，篩選的限制性就會比較低。</span><span class="sxs-lookup"><span data-stu-id="a074d-197">If you specify the most-derived type, it could be more restrictive; if you specify the root base type, it could be less restrictive.</span></span>  
  
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
  
### <a name="filter-by-activity-name-activity-type-user-data-type-and-user-key"></a><span data-ttu-id="a074d-198">依活動名稱、活動型別、使用者資料型別及使用者金鑰篩選</span><span class="sxs-lookup"><span data-stu-id="a074d-198">Filter by Activity Name, Activity Type, User Data Type, and User Key</span></span>  
 <span data-ttu-id="a074d-199">這種篩選會透過加入活動名稱，更進一步地限制活動型別、使用者資料型別及使用者金鑰模式。</span><span class="sxs-lookup"><span data-stu-id="a074d-199">This filter further restricts the activity type, user data type, and user key pattern by the addition of activity name.</span></span>  
  
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