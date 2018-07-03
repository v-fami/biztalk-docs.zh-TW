---
title: 失敗發生在處理 X12 訊息在傳送埠： 收件者及寄件者識別碼辨識符號配對不一致 |Microsoft Docs
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
ms.openlocfilehash: 8fa38616bfc4117614ab81d4a369f64d3b85e13f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988799"
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs"></a><span data-ttu-id="86040-102">失敗發生在處理 X12 訊息在傳送埠： 收件者及寄件者識別碼辨識符號配對不一致</span><span class="sxs-lookup"><span data-stu-id="86040-102">A failure occurred in processing X12 message on send port: No agreement for receiver and sender identifier-qualifier pairs</span></span>
## <a name="details"></a><span data-ttu-id="86040-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="86040-103">Details</span></span>  
  
|                 |                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="86040-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="86040-104">Product Name</span></span>   |                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                       |
| <span data-ttu-id="86040-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="86040-105">Product Version</span></span> |                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                   |
|    <span data-ttu-id="86040-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="86040-106">Event ID</span></span>     |                                                                               -                                                                               |
|  <span data-ttu-id="86040-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="86040-107">Event Source</span></span>   |                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="86040-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="86040-108"> EDI</span></span>                                     |
|    <span data-ttu-id="86040-109">元件</span><span class="sxs-lookup"><span data-stu-id="86040-109">Component</span></span>    |                                                                          <span data-ttu-id="86040-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="86040-110">EDI Engine</span></span>                                                                           |
|  <span data-ttu-id="86040-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="86040-111">Symbolic Name</span></span>  |                                                                               -                                                                               |
|  <span data-ttu-id="86040-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="86040-112">Message Text</span></span>   | <span data-ttu-id="86040-113">失敗發生在處理 X12 訊息傳送埠上的{0}。</span><span class="sxs-lookup"><span data-stu-id="86040-113">A failure occurred in processing X12 message on send port {0}.</span></span> <span data-ttu-id="86040-114">沒有協議的收件者及寄件者識別碼/辨識符號配對存在{1}， {2}， {3}， {4}。</span><span class="sxs-lookup"><span data-stu-id="86040-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="86040-115">說明</span><span class="sxs-lookup"><span data-stu-id="86040-115">Explanation</span></span>  
 <span data-ttu-id="86040-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 EDIFACT 交換因為 BizTalk Server 找不到符合升級傳送者辨識符號和識別項屬性，並提升接收者辨識符號和識別項屬性，與合作對象對應的值。</span><span class="sxs-lookup"><span data-stu-id="86040-116">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because BizTalk Server was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="86040-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="86040-117">User Action</span></span>  
 <span data-ttu-id="86040-118">若要解決這個錯誤，請確定傳送者辨識符號和識別項 （ISA5 和 ISA6） 和接收者辨識符號和識別碼 （ISA7 與 ISA8） 在 [EDI 屬性] 對話方塊中的合作對象的 [ISA 區段定義] 頁面中定義符合升級的對應交換的內容中的屬性。</span><span class="sxs-lookup"><span data-stu-id="86040-118">To resolve this error, ensure that the sender qualifier and identifier (ISA5 and ISA6) and receiver qualifier and identifier (ISA7 and ISA8) defined in the party's ISA Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>