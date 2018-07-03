---
title: 處理傳送埠上的 Edifact 訊息時發生錯誤： 收件者及寄件者識別碼辨識符號配對不一致 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cffc4705-164f-4779-8f04-c6a2a7f1bbda
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c27bc81b24a9d2850bc895f28020df286da17cba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021868"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs"></a><span data-ttu-id="59359-102">處理傳送埠上的 Edifact 訊息時發生錯誤： 收件者及寄件者識別碼辨識符號配對不一致</span><span class="sxs-lookup"><span data-stu-id="59359-102">A failure occurred in processing Edifact message on send port: No agreement for receiver and sender identifier-qualifier pairs</span></span>
## <a name="details"></a><span data-ttu-id="59359-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="59359-103">Details</span></span>  
  
|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="59359-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="59359-104">Product Name</span></span>   |                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                         |
| <span data-ttu-id="59359-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="59359-105">Product Version</span></span> |                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                     |
|    <span data-ttu-id="59359-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="59359-106">Event ID</span></span>     |                                                                                 -                                                                                 |
|  <span data-ttu-id="59359-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="59359-107">Event Source</span></span>   |                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="59359-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="59359-108"> EDI</span></span>                                       |
|    <span data-ttu-id="59359-109">元件</span><span class="sxs-lookup"><span data-stu-id="59359-109">Component</span></span>    |                                                                            <span data-ttu-id="59359-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="59359-110">EDI Engine</span></span>                                                                             |
|  <span data-ttu-id="59359-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="59359-111">Symbolic Name</span></span>  |                                                                                 -                                                                                 |
|  <span data-ttu-id="59359-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="59359-112">Message Text</span></span>   | <span data-ttu-id="59359-113">處理傳送埠上的 Edifact 訊息時發生失敗{0}。</span><span class="sxs-lookup"><span data-stu-id="59359-113">A failure occurred in processing Edifact message on send port {0}.</span></span> <span data-ttu-id="59359-114">沒有協議的收件者及寄件者識別碼/辨識符號配對存在{1}， {2}， {3}， {4}。</span><span class="sxs-lookup"><span data-stu-id="59359-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="59359-115">說明</span><span class="sxs-lookup"><span data-stu-id="59359-115">Explanation</span></span>  
 <span data-ttu-id="59359-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析 EDIFACT 交換的合作對象，因為它無法符合升級傳送者辨識符號和識別項屬性，並提升接收者辨識符號和識別項使用合作對象的對應值的屬性。</span><span class="sxs-lookup"><span data-stu-id="59359-116">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because it was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59359-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="59359-117">User Action</span></span>  
 <span data-ttu-id="59359-118">若要解決這個錯誤，請確定傳送者辨識符號和識別項 （UNB2.1 和 UNB2.2） 和接收者辨識符號和識別 （UNB3.1 和 UNB3.2） 在 [EDI 屬性] 對話方塊中的合作對象的 [UNB 區段定義] 頁面中定義符合對應交換的內容中的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="59359-118">To resolve this error, ensure that the sender qualifier and identifier (UNB2.1 and UNB2.2) and receiver qualifier and identifier (UNB3.1 and UNB3.2) defined in the party's UNB Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>