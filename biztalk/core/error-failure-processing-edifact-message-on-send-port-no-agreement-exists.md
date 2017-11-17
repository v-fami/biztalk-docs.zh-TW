---
title: "在處理傳送埠上的 Edifact 訊息發生失敗： 沒有接收者和傳送者識別碼辨識符號組和名稱的任何合作對象的協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11880c7c-6032-449b-b251-27fc2b2f0d72
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7df88a39d9ccbbcd94fd4498c5847c5104bb40cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a><span data-ttu-id="4dd7d-102">在處理傳送埠上的 Edifact 訊息發生失敗： 沒有接收者和傳送者識別碼辨識符號組和名稱的任何合作對象的協議</span><span class="sxs-lookup"><span data-stu-id="4dd7d-102">A failure occurred in processing Edifact message on send port: No agreement for receiver and sender identifier-qualifier pairs and no party with name</span></span>
## <a name="details"></a><span data-ttu-id="4dd7d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4dd7d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4dd7d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4dd7d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4dd7d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4dd7d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4dd7d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4dd7d-106">Event ID</span></span>|-|  
|<span data-ttu-id="4dd7d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4dd7d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4dd7d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="4dd7d-108"> EDI</span></span>|  
|<span data-ttu-id="4dd7d-109">元件</span><span class="sxs-lookup"><span data-stu-id="4dd7d-109">Component</span></span>|<span data-ttu-id="4dd7d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="4dd7d-110">EDI Engine</span></span>|  
|<span data-ttu-id="4dd7d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4dd7d-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="4dd7d-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4dd7d-112">Message Text</span></span>|<span data-ttu-id="4dd7d-113">在處理傳送埠 {0} 上的 Edifact 訊息發生失敗。</span><span class="sxs-lookup"><span data-stu-id="4dd7d-113">A failure occurred in processing Edifact message on send port {0}.</span></span> <span data-ttu-id="4dd7d-114">{1}、 {2}、 {3}、 \ {4 的收件者和寄件者識別碼/辨識符號配對不存在任何協議。</span><span class="sxs-lookup"><span data-stu-id="4dd7d-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span> <span data-ttu-id="4dd7d-115">沒有合作對象名稱 {5} 存在。</span><span class="sxs-lookup"><span data-stu-id="4dd7d-115">No Party exists with name {5}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4dd7d-116">說明</span><span class="sxs-lookup"><span data-stu-id="4dd7d-116">Explanation</span></span>  
 <span data-ttu-id="4dd7d-117">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析 EDIFACT 交換的合作對象，因為它無法符合升級寄件者辨識符號和識別項屬性和升級接收者辨識符號和識別項使用合作對象的對應值的屬性。</span><span class="sxs-lookup"><span data-stu-id="4dd7d-117">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because it was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4dd7d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4dd7d-118">User Action</span></span>  
 <span data-ttu-id="4dd7d-119">若要解決這個錯誤，請確定傳送者辨識符號和識別 （UNB2.1 和 UNB2.2） 和接收者辨識符號和識別 （UNB3.1 和 UNB3.2） 合作對象的 UNB 區段定義 頁面的 EDI 屬性 對話方塊中定義符合對應交換的內容中的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="4dd7d-119">To resolve this error, ensure that the sender qualifier and identifier (UNB2.1 and UNB2.2) and receiver qualifier and identifier (UNB3.1 and UNB3.2) defined in the party's UNB Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>