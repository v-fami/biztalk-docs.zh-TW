---
title: "發現無法辨識的訊息類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4094bf-af00-4d5c-9661-7c8abcb1b722
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd58907b61e68140ccf68d8256882b81e46bd863
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognised-message-type"></a><span data-ttu-id="41f5f-102">無法辨識的訊息類型</span><span class="sxs-lookup"><span data-stu-id="41f5f-102">Unrecognised message type</span></span>
## <a name="details"></a><span data-ttu-id="41f5f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="41f5f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41f5f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="41f5f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="41f5f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="41f5f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="41f5f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="41f5f-106">Event ID</span></span>|-|  
|<span data-ttu-id="41f5f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="41f5f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="41f5f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="41f5f-108"> EDI</span></span>|  
|<span data-ttu-id="41f5f-109">元件</span><span class="sxs-lookup"><span data-stu-id="41f5f-109">Component</span></span>|<span data-ttu-id="41f5f-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="41f5f-110">EDI Engine</span></span>|  
|<span data-ttu-id="41f5f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="41f5f-111">Symbolic Name</span></span>|<span data-ttu-id="41f5f-112">UnRecognizedMessageType</span><span class="sxs-lookup"><span data-stu-id="41f5f-112">UnRecognizedMessageType</span></span>|  
|<span data-ttu-id="41f5f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="41f5f-113">Message Text</span></span>|<span data-ttu-id="41f5f-114">無法辨識的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="41f5f-114">Unrecognised message type.</span></span> <span data-ttu-id="41f5f-115">無法進一步處理。</span><span class="sxs-lookup"><span data-stu-id="41f5f-115">Cannot proceed further.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41f5f-116">說明</span><span class="sxs-lookup"><span data-stu-id="41f5f-116">Explanation</span></span>  
 <span data-ttu-id="41f5f-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為沒有文件結構描述文件類型的交易集在該交換中，已部署或 BizTalk Server 無法判斷文件類型的交易從交易集識別項代碼、 版本和命名空間。</span><span class="sxs-lookup"><span data-stu-id="41f5f-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because no document schema has been deployed for the document type of a transaction set in that interchange, or BizTalk Server cannot determine the document type from the transaction set identifier code, version, and namespace.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41f5f-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="41f5f-118">User Action</span></span>  
 <span data-ttu-id="41f5f-119">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="41f5f-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="41f5f-120">部署交換中交易集的文件類型的文件結構描述，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="41f5f-120">Deploy a document schema for the document type of a transaction set in the interchange, and then resend the interchange.</span></span>  
  
-   <span data-ttu-id="41f5f-121">請確認下列的值定義有效的結構描述： 對於 X12，目標命名空間、 版本/版次和文件類型。對於 EDIFACT，目標命名空間、 訊息版本號碼、 訊息版次號碼和訊息類型。</span><span class="sxs-lookup"><span data-stu-id="41f5f-121">Verify that the following values define a valid schema: for X12, the target namespace, version/release, and document type; for EDIFACT, the target namespace, message version number, message release number, and message type.</span></span> <span data-ttu-id="41f5f-122">如需詳細資訊，請參閱 「 結構描述探索 」 一節中的 「 合作對象解析、 結構描述探索和接收 EDI 訊息的授權 」 主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="41f5f-122">For more information, see the "Schema Discovery" section in the "Party Resolution, Schema Discovery, and Authorization for Received EDI Messages" topic in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>