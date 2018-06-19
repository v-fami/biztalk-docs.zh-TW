---
title: 失敗發生在處理 X12 傳送埠上的訊息： 接收者和傳送者識別碼辨識符號組沒有協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72ae7926-f5c1-42f4-8c29-11f34c138dd4
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 637cd174b2c9723f4391417392700e3a4f079b79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240854"
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs"></a><span data-ttu-id="0db85-102">失敗發生在處理 X12 傳送埠上的訊息： 接收者和傳送者識別碼辨識符號組沒有協議</span><span class="sxs-lookup"><span data-stu-id="0db85-102">A failure occurred in processing X12 message on send port: No agreement for receiver and sender identifier-qualifier pairs</span></span>
## <a name="details"></a><span data-ttu-id="0db85-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0db85-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0db85-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0db85-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0db85-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0db85-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0db85-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0db85-106">Event ID</span></span>|-|  
|<span data-ttu-id="0db85-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0db85-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0db85-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0db85-108"> EDI</span></span>|  
|<span data-ttu-id="0db85-109">元件</span><span class="sxs-lookup"><span data-stu-id="0db85-109">Component</span></span>|<span data-ttu-id="0db85-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0db85-110">EDI Engine</span></span>|  
|<span data-ttu-id="0db85-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0db85-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="0db85-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0db85-112">Message Text</span></span>|<span data-ttu-id="0db85-113">失敗發生在處理 X12 訊息傳送連接埠 {0}。</span><span class="sxs-lookup"><span data-stu-id="0db85-113">A failure occurred in processing X12 message on send port {0}.</span></span> <span data-ttu-id="0db85-114">{1}、 {2}、 {3}、 \ {4 的收件者和寄件者識別碼/辨識符號配對不存在任何協議。</span><span class="sxs-lookup"><span data-stu-id="0db85-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0db85-115">說明</span><span class="sxs-lookup"><span data-stu-id="0db85-115">Explanation</span></span>  
 <span data-ttu-id="0db85-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 EDIFACT 交換，因為 BizTalk Server 無法符合升級寄件者辨識符號和識別項屬性和升級接收者辨識符號和識別項屬性，與合作對象的對應值。</span><span class="sxs-lookup"><span data-stu-id="0db85-116">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because BizTalk Server was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0db85-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0db85-117">User Action</span></span>  
 <span data-ttu-id="0db85-118">若要解決這個錯誤，請確定傳送者辨識符號和識別項 （ISA5 和 ISA6） 和接收者辨識符號和識別碼 （ISA7 和 ISA8） 合作對象的 ISA 區段定義 頁面的 EDI 屬性 對話方塊中定義符合升級的對應交換的內容中的屬性。</span><span class="sxs-lookup"><span data-stu-id="0db85-118">To resolve this error, ensure that the sender qualifier and identifier (ISA5 and ISA6) and receiver qualifier and identifier (ISA7 and ISA8) defined in the party's ISA Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>