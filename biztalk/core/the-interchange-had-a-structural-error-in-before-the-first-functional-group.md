---
title: "交換發生結構錯誤的第一個功能群組之前 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ab490de214f53e85ea32c1b243456f837c72e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-a-structural-error-in-before-the-first-functional-group"></a><span data-ttu-id="3f130-102">交換發生結構錯誤的第一個功能群組之前</span><span class="sxs-lookup"><span data-stu-id="3f130-102">The interchange had a structural error in-before the first functional group</span></span>
## <a name="details"></a><span data-ttu-id="3f130-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3f130-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f130-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3f130-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3f130-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3f130-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3f130-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3f130-106">Event ID</span></span>|-|  
|<span data-ttu-id="3f130-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3f130-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3f130-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3f130-108"> EDI</span></span>|  
|<span data-ttu-id="3f130-109">元件</span><span class="sxs-lookup"><span data-stu-id="3f130-109">Component</span></span>|<span data-ttu-id="3f130-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3f130-110">EDI Engine</span></span>|  
|<span data-ttu-id="3f130-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3f130-111">Symbolic Name</span></span>|<span data-ttu-id="3f130-112">X12InterchangeStructuralErrorBefore1stGroup</span><span class="sxs-lookup"><span data-stu-id="3f130-112">X12InterchangeStructuralErrorBefore1stGroup</span></span>|  
|<span data-ttu-id="3f130-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3f130-113">Message Text</span></span>|<span data-ttu-id="3f130-114">交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 必須在/之前第一個功能群組的結構錯誤</span><span class="sxs-lookup"><span data-stu-id="3f130-114">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error in/before the first functional group</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f130-115">說明</span><span class="sxs-lookup"><span data-stu-id="3f130-115">Explanation</span></span>  
 <span data-ttu-id="3f130-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換中，其中一個原因如下：</span><span class="sxs-lookup"><span data-stu-id="3f130-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, for one of the following reasons:</span></span>  
  
-   <span data-ttu-id="3f130-117">結構的錯誤發生的 ISA 和 IEA 區段或交換的第一個的功能群組中，因此適用的結構描述不符合交換。</span><span class="sxs-lookup"><span data-stu-id="3f130-117">A structural error occurred in either the ISA and IEA segments or the first functional group of the interchange, so the interchange did not conform to the applicable schema.</span></span>  
  
-   <span data-ttu-id="3f130-118">未部署的 X12ServiceSchema （在 BaseArtifacts.dll)。</span><span class="sxs-lookup"><span data-stu-id="3f130-118">The X12ServiceSchema (in BaseArtifacts.dll) was not deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f130-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3f130-119">User Action</span></span>  
 <span data-ttu-id="3f130-120">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3f130-120">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="3f130-121">交換變更 ISA 的寄件者及/或 IEA 區段或第一次的功能群組，使其符合適用的結構描述，而且再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="3f130-121">Have the sender of the interchange change the ISA and/or IEA segments or the first functional group so that it conforms to the applicable schema, and then resend the interchange.</span></span>  
  
-   <span data-ttu-id="3f130-122">請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。</span><span class="sxs-lookup"><span data-stu-id="3f130-122">Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed.</span></span> <span data-ttu-id="3f130-123">您可以藉由開啟 BizTalk Server 管理主控台，開啟 [BizTalk EDI 應用程式] 節點和 [結構描述] 節點中，確認 X12ServiceSchema 列。</span><span class="sxs-lookup"><span data-stu-id="3f130-123">You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and the Schemas node, and verifying that X12ServiceSchema is listed.</span></span>