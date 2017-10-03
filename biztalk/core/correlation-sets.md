---
title: "相互關聯集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, inspecting
- correlation sets, about correlation sets
- correlation sets, passing as parameters
- messages, correlation sets
- correlation sets
- correlation sets, following correlation sets
- correlation sets, initializing
ms.assetid: 528dcd6c-d364-4bb8-8deb-cd4a0791867f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28d11e5e174808ca7718d5fef98b3ad079cffc18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlation-sets"></a><span data-ttu-id="7d192-102">相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="7d192-102">Correlation Sets</span></span>
<span data-ttu-id="7d192-103">您可以定義相互關聯集合以達成訊息與協調流程執行個體的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7d192-103">You can achieve this sort of correlation of messages with orchestration instances by defining correlation sets.</span></span> <span data-ttu-id="7d192-104">相互關聯集是一組屬性*具有特定值*。</span><span class="sxs-lookup"><span data-stu-id="7d192-104">A correlation set is a set of properties *with specific values*.</span></span> <span data-ttu-id="7d192-105">這是相互關聯類型，也就是只是一份屬性不同。</span><span class="sxs-lookup"><span data-stu-id="7d192-105">This is different from a correlation type, which is simply a list of properties.</span></span> <span data-ttu-id="7d192-106">如果傳入的訊息沒有所有這些屬性，並在每個屬性都有相符的值，相互關聯便會失敗，而且訊息也不會由協調流程執行個體所接收。</span><span class="sxs-lookup"><span data-stu-id="7d192-106">If an incoming message does not have all of these properties, with matching values for each, correlation will fail and the message will not be received by the orchestration instance.</span></span>  
  
 <span data-ttu-id="7d192-107">相互關聯類型定義屬性的集合，您會在此集合上使訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7d192-107">Correlation types define a set of properties on which you will be correlating messages.</span></span> <span data-ttu-id="7d192-108">這些可以是先前在屬性結構描述中定義，以及使用某些 BizTalk 專案部署的屬性，其中包括以 GlobalPropertySchemas (安裝為基本 BizTalk 安裝的一部分) 部署的「系統」屬性，</span><span class="sxs-lookup"><span data-stu-id="7d192-108">These can be any properties which were previously defined in a property schema and deployed with some BizTalk Project including "system" properties deployed with the GlobalPropertySchemas which is installed as part of the base BizTalk install.</span></span> <span data-ttu-id="7d192-109">相互關聯集合會定義一組屬性以及這些屬性的值，訊息必須包含這個組合才可以交由特定的協調流程處理。</span><span class="sxs-lookup"><span data-stu-id="7d192-109">A correlation set defines a set of properties and values for these properties that a message must contain to be processed by a particular orchestration.</span></span>  
  
 <span data-ttu-id="7d192-110">例如，相互關聯類型可能由下列屬性組成：</span><span class="sxs-lookup"><span data-stu-id="7d192-110">For example, a correlation type could consist of the following properties:</span></span>  
  
|<span data-ttu-id="7d192-111">相互關聯類型屬性</span><span class="sxs-lookup"><span data-stu-id="7d192-111">Correlation Type Property</span></span>|<span data-ttu-id="7d192-112">可能的 XML 表示法</span><span class="sxs-lookup"><span data-stu-id="7d192-112">Possible XML Representation</span></span>|  
|-------------------------------|---------------------------------|  
|<span data-ttu-id="7d192-113">社會安全碼</span><span class="sxs-lookup"><span data-stu-id="7d192-113">Social Security number</span></span>|<span data-ttu-id="7d192-114">\<SSN >\</SSN ></span><span class="sxs-lookup"><span data-stu-id="7d192-114">\<SSN>\</SSN></span></span>|  
|<span data-ttu-id="7d192-115">生日</span><span class="sxs-lookup"><span data-stu-id="7d192-115">Date of Birth</span></span>|<span data-ttu-id="7d192-116">\<DOB >\</DOB ></span><span class="sxs-lookup"><span data-stu-id="7d192-116">\<DOB>\</DOB></span></span>|  
|<span data-ttu-id="7d192-117">Gender</span><span class="sxs-lookup"><span data-stu-id="7d192-117">Gender</span></span>|<span data-ttu-id="7d192-118">\<性別 >\<性別/></span><span class="sxs-lookup"><span data-stu-id="7d192-118">\<Gender>\</Gender></span></span>|  
  
 <span data-ttu-id="7d192-119">衍生自此相互關聯類型的相互關聯集合則可能由下列屬性與值組成：</span><span class="sxs-lookup"><span data-stu-id="7d192-119">While a correlation set derived from this correlation type could consist of the following properties and values:</span></span>  
  
|<span data-ttu-id="7d192-120">相互關聯集合屬性/值</span><span class="sxs-lookup"><span data-stu-id="7d192-120">Correlation Set Property/Value</span></span>|<span data-ttu-id="7d192-121">可能的 XML 表示法</span><span class="sxs-lookup"><span data-stu-id="7d192-121">Possible XML representation</span></span>|  
|-------------------------------------|---------------------------------|  
|<span data-ttu-id="7d192-122">社會安全碼 = 222112222</span><span class="sxs-lookup"><span data-stu-id="7d192-122">Social Security number = 222112222</span></span>|<span data-ttu-id="7d192-123">\<SSN > 222112222\</SSN ></span><span class="sxs-lookup"><span data-stu-id="7d192-123">\<SSN>222112222\</SSN></span></span>|  
|<span data-ttu-id="7d192-124">生日 = “1/1/1995”</span><span class="sxs-lookup"><span data-stu-id="7d192-124">Date of Birth = “1/1/1995”</span></span>|<span data-ttu-id="7d192-125">\<DOB >"1/1/1995"\</DOB ></span><span class="sxs-lookup"><span data-stu-id="7d192-125">\<DOB>”1/1/1995”\</DOB></span></span>|  
|<span data-ttu-id="7d192-126">性別 = 男</span><span class="sxs-lookup"><span data-stu-id="7d192-126">Gender = Male</span></span>|<span data-ttu-id="7d192-127">\<性別 > M\<性別/></span><span class="sxs-lookup"><span data-stu-id="7d192-127">\<Gender>M\</Gender></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="7d192-128">每個相互關聯集合最多可支援三個參數。</span><span class="sxs-lookup"><span data-stu-id="7d192-128">Each correlation set supports a maximum of three parameters.</span></span>  
  
## <a name="initializing-correlation-sets"></a><span data-ttu-id="7d192-129">初始化相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="7d192-129">Initializing Correlation Sets</span></span>  
  
-   <span data-ttu-id="7d192-130">**接收動作上初始化的相互關聯集**</span><span class="sxs-lookup"><span data-stu-id="7d192-130">**Correlation Sets initialized on a Receive action**</span></span>  
  
     <span data-ttu-id="7d192-131">在接收動作上初始化的相互關聯集合會定義必須存在於發佈訊息中的確切屬性組，以便使其由協調流程中的對應接收動作處理。</span><span class="sxs-lookup"><span data-stu-id="7d192-131">Correlation sets initialized on a Receive action define the exact set of properties that must exist in a published message in order for it to be processed by the corresponding receive action(s) in an orchestration.</span></span> <span data-ttu-id="7d192-132">初始化的相互關聯集合會根據文件中的對應值，從相互關聯類型建立相互關聯集合。</span><span class="sxs-lookup"><span data-stu-id="7d192-132">An initializing correlation set will create a correlation set from a correlation type based on the corresponding values in a document.</span></span>  
  
-   <span data-ttu-id="7d192-133">**傳送動作上初始化的相互關聯集**</span><span class="sxs-lookup"><span data-stu-id="7d192-133">**Correlation Sets initialized on a Send action**</span></span>  
  
     <span data-ttu-id="7d192-134">在傳送動作上初始化的相互關聯集合會根據文件中的對應值，從相互關聯類型建立，並會升級在輸出文件中的相互關聯屬性。</span><span class="sxs-lookup"><span data-stu-id="7d192-134">Correlation sets initialized on a Send action are created from a correlation type based upon the corresponding values in a document and promote the correlation properties in the outbound document.</span></span>  
  
## <a name="following-correlation-sets"></a><span data-ttu-id="7d192-135">沿用相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="7d192-135">Following Correlation Sets</span></span>  
 <span data-ttu-id="7d192-136">沿用相互關聯集合只能繫結至非啟動的接收動作或傳送動作。</span><span class="sxs-lookup"><span data-stu-id="7d192-136">Following correlation sets can only be bound to a non-activating receive action or to a send action.</span></span> <span data-ttu-id="7d192-137">沿用相互關聯集合是在與先前初始化之相互關聯集合的匯接中指定的。</span><span class="sxs-lookup"><span data-stu-id="7d192-137">Following correlation sets are specified in tandem with previously initialized correlation sets.</span></span>  
  
-   <span data-ttu-id="7d192-138">**繫結至接收動作的沿用相互關聯集**</span><span class="sxs-lookup"><span data-stu-id="7d192-138">**Following Correlation Sets bound to a Receive action**</span></span>  
  
     <span data-ttu-id="7d192-139">繫結至接收動作的沿用相互關聯集合會定義一組文件必須包含的屬性及其值才能被接收。</span><span class="sxs-lookup"><span data-stu-id="7d192-139">Following correlation sets bound to a receive action define the set of properties and values that the document must contain to be received.</span></span>  <span data-ttu-id="7d192-140">沿用相互關聯集合的接收動作會接受包含先前初始化之相互關聯集合中屬性的文件。</span><span class="sxs-lookup"><span data-stu-id="7d192-140">Receive actions with following correlation sets accept documents that contain properties from a previously initialized correlation set.</span></span>  
  
-   <span data-ttu-id="7d192-141">**繫結至傳送動作的沿用相互關聯集**</span><span class="sxs-lookup"><span data-stu-id="7d192-141">**Following Correlation Sets bound to a Send action**</span></span>  
  
     <span data-ttu-id="7d192-142">繫結至傳送動作的沿用相互關聯集合指示相互關聯集合中的屬性組會在輸出的文件中升級。</span><span class="sxs-lookup"><span data-stu-id="7d192-142">Following correlation sets bound to a send action dictate that the set of properties in the correlation set are promoted in the outbound document.</span></span>  
  
## <a name="inspecting-correlation-sets"></a><span data-ttu-id="7d192-143">檢查相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="7d192-143">Inspecting Correlation Sets</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7d192-144"> 提供檢查相互關聯集合的能力。</span><span class="sxs-lookup"><span data-stu-id="7d192-144"> provides the ability to inspect correlation sets.</span></span> <span data-ttu-id="7d192-145">您可以使用與下列相似的程式碼，在「運算式圖形」中檢查相互關聯集合：</span><span class="sxs-lookup"><span data-stu-id="7d192-145">You can inspect a correlation set in an Expression Shape using code similar to the following:</span></span>  
  
```  
MsgLen = Correlation_1(BTS.MessageLength);  
```  
  
 <span data-ttu-id="7d192-146">上述範例假設您已建立名為的變數**MsgLen**型別的**System.Int16**和您的協調流程包含相互關聯集具名**Correlation_1**.</span><span class="sxs-lookup"><span data-stu-id="7d192-146">The example above assumes that you have created a variable named **MsgLen** of type **System.Int16** and that your orchestration contains a correlation set named **Correlation_1**.</span></span> <span data-ttu-id="7d192-147">如果您需要檢查由一個協調流程傳遞至另一個協調流程之相互關聯的值，檢查相互關聯集合這個功能相當有用。</span><span class="sxs-lookup"><span data-stu-id="7d192-147">The ability to inspect correlation sets may be useful if you need to inspect the value of a correlation that was passed to an orchestration by another orchestration.</span></span>  
  
## <a name="passing-correlation-sets-as-parameters-to-orchestrations"></a><span data-ttu-id="7d192-148">將相互關聯集合當做參數傳遞至協調流程。</span><span class="sxs-lookup"><span data-stu-id="7d192-148">Passing Correlation Sets as Parameters to Orchestrations</span></span>  
 <span data-ttu-id="7d192-149">您可以傳遞相互關聯當做*中*至其他協調流程的參數。</span><span class="sxs-lookup"><span data-stu-id="7d192-149">You can pass correlations as *in* parameters to other orchestrations.</span></span>