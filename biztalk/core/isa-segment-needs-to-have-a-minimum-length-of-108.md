---
title: "ISA 區段必須有最小長度為 108 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57641445-cebb-4219-998d-54038d7ddf19
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ecd5c6761c6dbcc59ad6353efa2772b9eecf387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="isa-segment-needs-to-have-a-minimum-length-of-108"></a><span data-ttu-id="e9878-102">ISA 區段的長度至少要有 108</span><span class="sxs-lookup"><span data-stu-id="e9878-102">ISA segment needs to have a minimum length of 108</span></span>
## <a name="details"></a><span data-ttu-id="e9878-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e9878-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9878-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e9878-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e9878-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e9878-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e9878-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e9878-106">Event ID</span></span>|-|  
|<span data-ttu-id="e9878-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e9878-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e9878-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e9878-108"> EDI</span></span>|  
|<span data-ttu-id="e9878-109">元件</span><span class="sxs-lookup"><span data-stu-id="e9878-109">Component</span></span>|<span data-ttu-id="e9878-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e9878-110">EDI Engine</span></span>|  
|<span data-ttu-id="e9878-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e9878-111">Symbolic Name</span></span>|<span data-ttu-id="e9878-112">NseIsaSuffix1LFDescription</span><span class="sxs-lookup"><span data-stu-id="e9878-112">NseIsaSuffix1LFDescription</span></span>|  
|<span data-ttu-id="e9878-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e9878-113">Message Text</span></span>|<span data-ttu-id="e9878-114">ISA 區段必須有 108 最小長度、 執行個體有 {0}</span><span class="sxs-lookup"><span data-stu-id="e9878-114">ISA segment needs to have a minimum length of 108, instance has {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e9878-115">說明</span><span class="sxs-lookup"><span data-stu-id="e9878-115">Explanation</span></span>  
 <span data-ttu-id="e9878-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為服務結構描述所建立的數字的數目不符合交換中的 ISA 區段 (X12ServiceSchema 或EdifactServiceSchema BaseArtifacts.dll 中)。</span><span class="sxs-lookup"><span data-stu-id="e9878-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the ISA segment in the interchange did not conform to the number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e9878-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e9878-117">User Action</span></span>  
 <span data-ttu-id="e9878-118">若要解決這個錯誤，請確定每個欄位 （從 ISA01 到 ISA16) ISA 區段中具有所需的一位數的最小數目。</span><span class="sxs-lookup"><span data-stu-id="e9878-118">To resolve this error, make sure that each of the fields in the ISA segment (from ISA01 to ISA16) has the required minimum number of digits.</span></span> <span data-ttu-id="e9878-119">您可以開啟 BizTalk Server 管理主控台中，查看數字的最小數目開啟 BizTalk 群組 節點、 應用程式 節點、 BizTalk EDI 應用程式 節點，和結構描述 節點中。開啟 Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema ISA; 根節點然後按一下 結構描述檢視。</span><span class="sxs-lookup"><span data-stu-id="e9878-119">You can see the minimum number of digits by opening the BizTalk Server Administration Console; opening the BizTalk Group node, the Applications node, the BizTalk EDI Application node, and then the schema node; opening the Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema with the root node of ISA; and then clicking the Schema View.</span></span>