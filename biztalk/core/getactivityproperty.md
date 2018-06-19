---
title: GetActivityProperty |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2321f1ec-d98d-478f-bb1d-a11a98e60fa5
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55f0d24da85088fb8f13693c8c71d32bee1bef7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246582"
---
# <a name="getactivityproperty"></a><span data-ttu-id="870f5-102">GetActivityProperty</span><span class="sxs-lookup"><span data-stu-id="870f5-102">GetActivityProperty</span></span>
<span data-ttu-id="870f5-103">將從與追蹤事件相關的活動所擷取的屬性推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="870f5-103">Pushes the extracted property from the activity related to the tracking event onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="870f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="870f5-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="870f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="870f5-105">Parameters</span></span>  
 <span data-ttu-id="870f5-106">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="870f5-106">Name of the property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="870f5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="870f5-107">Return Value</span></span>  
 <span data-ttu-id="870f5-108">包含屬性值的字串。</span><span class="sxs-lookup"><span data-stu-id="870f5-108">String containing the value of the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="870f5-109">備註</span><span class="sxs-lookup"><span data-stu-id="870f5-109">Remarks</span></span>  
 <span data-ttu-id="870f5-110">您可以使用點標記法來限定要擷取的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="870f5-110">You can use dotted-notation for qualifying the property name you want to retrieve.</span></span> <span data-ttu-id="870f5-111">以便存取透過屬性所公開的其他物件內的物件。</span><span class="sxs-lookup"><span data-stu-id="870f5-111">This will provide you access to objects inside of other objects exposed through properties.</span></span> <span data-ttu-id="870f5-112">例如，若要存取訂單之 Address 執行個體的 City 屬性，請使用 "purchaseOrder.Address.City"。</span><span class="sxs-lookup"><span data-stu-id="870f5-112">For example, to access the City property of an Address instance of a purchase order, use "purchaseOrder.Address.City".</span></span>  
  
 <span data-ttu-id="870f5-113">屬性名稱會先區分大小寫，然後不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="870f5-113">Property names are case-sensitive first, and then case-insensitive.</span></span> <span data-ttu-id="870f5-114">當您的 WF 應用程式中有兩個以上只有大小寫不同的活動屬性時，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="870f5-114">This is important when you have two or more activity properties that vary only by case in your WF application.</span></span> <span data-ttu-id="870f5-115">例如，如果工作流程應用程式中已定義屬性 "myWorkflow" 和 "MyWorkflow"，而且您要尋找 "MyWorkflow"，透過區分大小寫比對，會找到相符的第二個屬性。</span><span class="sxs-lookup"><span data-stu-id="870f5-115">For example, if your workflow application has the properties "myWorkflow" and "MyWorkflow" defined and you were looking for "MyWorkflow", it would match on the second property through a case-sensitive match.</span></span> <span data-ttu-id="870f5-116">如果您指定 "MYWORKFLOW"，在區分大小寫的比對嘗試失敗之後，會透過不區分大小寫比對，找到相符的 "myWorkflow"。</span><span class="sxs-lookup"><span data-stu-id="870f5-116">If you specify "MYWORKFLOW", it would match "myWorkflow" through a case-insensitive match after a case-sensitive match attempt fails.</span></span>  
  
 <span data-ttu-id="870f5-117">如果您有兩個活動屬性只能由不同的案例，例如:"myProperty"和"MyProperty"。</span><span class="sxs-lookup"><span data-stu-id="870f5-117">For example, if you have two activity properties that vary only by case: "myProperty" and "MyProperty".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="870f5-118">NULL 屬性值會導致 NullReferenceException 擲回到工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="870f5-118">NULL property values will result in a NullReferenceException being thrown back to the workflow instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="870f5-119">範例</span><span class="sxs-lookup"><span data-stu-id="870f5-119">Example</span></span>  
 <span data-ttu-id="870f5-120">在下列範例中，更新運算式會藉由使用 `GetActivityProperty`，保存活動屬性 "MyProperty"。</span><span class="sxs-lookup"><span data-stu-id="870f5-120">In the following sample, an update expression is used to persist the activity property "MyProperty" by using `GetActivityProperty`.</span></span>  
  
```  
<ic:Update DataItemName="TextData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetActivityProperty">  
      <wf:Argument>MyProperty</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```