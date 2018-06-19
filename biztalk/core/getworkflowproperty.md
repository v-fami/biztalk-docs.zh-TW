---
title: GetWorkflowProperty |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9d3029e-3267-46bc-ba2e-1c6fa1f2e931
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505fc41ce544cdf16e3826116514ba1991ba012e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246430"
---
# <a name="getworkflowproperty"></a><span data-ttu-id="53b13-102">GetWorkflowProperty</span><span class="sxs-lookup"><span data-stu-id="53b13-102">GetWorkflowProperty</span></span>
<span data-ttu-id="53b13-103">將擷取自工作流程之根活動的屬性推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="53b13-103">Pushes the extracted property from the root activity of the workflow onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b13-104">語法</span><span class="sxs-lookup"><span data-stu-id="53b13-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53b13-105">參數</span><span class="sxs-lookup"><span data-stu-id="53b13-105">Parameters</span></span>  
 <span data-ttu-id="53b13-106">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="53b13-106">Name of the property.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="53b13-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="53b13-107">Pushed Value</span></span>  
 <span data-ttu-id="53b13-108">包含屬性值的字串。</span><span class="sxs-lookup"><span data-stu-id="53b13-108">String containing the value of the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53b13-109">備註</span><span class="sxs-lookup"><span data-stu-id="53b13-109">Remarks</span></span>  
 <span data-ttu-id="53b13-110">這項作業只適用於「更新」。</span><span class="sxs-lookup"><span data-stu-id="53b13-110">This operation is only valid in Updates.</span></span>  
  
 <span data-ttu-id="53b13-111">您可以使用點標記法來限定要擷取的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="53b13-111">You can use dotted-notation for qualifying the property name you want to retrieve.</span></span> <span data-ttu-id="53b13-112">以便存取透過屬性所公開的其他物件內的物件。</span><span class="sxs-lookup"><span data-stu-id="53b13-112">This will provide you access to objects inside of other objects exposed through properties.</span></span> <span data-ttu-id="53b13-113">例如，若要存取訂單之 Address 執行個體的 City 屬性，請使用 "purchaseOrder.Address.City"。</span><span class="sxs-lookup"><span data-stu-id="53b13-113">For example, to access the City property of an Address instance of a purchase order, use "purchaseOrder.Address.City".</span></span>  
  
 <span data-ttu-id="53b13-114">屬性名稱會先區分大小寫，然後不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="53b13-114">Property names are case-sensitive first, and then case-insensitive.</span></span> <span data-ttu-id="53b13-115">當您的 WF 應用程式中有兩個以上只有大小寫不同的活動屬性時，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="53b13-115">This is important when you have two or more activity properties that vary only by case in your WF application.</span></span> <span data-ttu-id="53b13-116">例如，如果工作流程應用程式中已定義屬性 "myWorkflow" 和 "MyWorkflow"，而且您要尋找 "MyWorkflow"，透過區分大小寫比對，會找到相符的第二個屬性。</span><span class="sxs-lookup"><span data-stu-id="53b13-116">For example, if your workflow application has the properties "myWorkflow" and "MyWorkflow" defined and you were looking for "MyWorkflow", it would match on the second property through a case-sensitive match.</span></span> <span data-ttu-id="53b13-117">如果您指定 "MYWORKFLOW"，在不區分大小寫的比對嘗試失敗之後，會透過區分大小寫比對，找到相符的 "myWorkflow"。</span><span class="sxs-lookup"><span data-stu-id="53b13-117">If you specify "MYWORKFLOW", it would match "myWorkflow" through a case-sensitive match after a case-insensitive match attempt fails.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53b13-118">NULL 屬性值會導致 NullReferenceException 擲回到工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="53b13-118">NULL property values will result in a NullReferenceException being thrown back to the workflow instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53b13-119">範例</span><span class="sxs-lookup"><span data-stu-id="53b13-119">Example</span></span>  
 <span data-ttu-id="53b13-120">下列範例將會使用更新運算式，保存應用 `GetWorkflowProperty` 從訂單取得的工作流程屬性 "City"。</span><span class="sxs-lookup"><span data-stu-id="53b13-120">In the following sample, an update expression is used to persist the workflow property "City" from a purchase order by using `GetWorkflowProperty`.</span></span>  
  
```  
<ic:Update DataItemName="City" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>po.Info.City</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```