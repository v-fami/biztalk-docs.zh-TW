---
title: 處理傳送埠上的 Edifact 訊息時發生錯誤： 沒有名稱的合作對象的收件者及寄件者識別碼辨識符號配對不一致 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11880c7c-6032-449b-b251-27fc2b2f0d72
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0b4e66ce918f59502125e77b7c19615cb281660
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009911"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a><span data-ttu-id="d28cc-102">處理傳送埠上的 Edifact 訊息時發生錯誤： 沒有名稱的合作對象的收件者及寄件者識別碼辨識符號配對不一致</span><span class="sxs-lookup"><span data-stu-id="d28cc-102">A failure occurred in processing Edifact message on send port: No agreement for receiver and sender identifier-qualifier pairs and no party with name</span></span>
## <a name="details"></a><span data-ttu-id="d28cc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d28cc-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d28cc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d28cc-104">Product Name</span></span>   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                        |
| <span data-ttu-id="d28cc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d28cc-105">Product Version</span></span> |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                    |
|    <span data-ttu-id="d28cc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d28cc-106">Event ID</span></span>     |                                                                                                -                                                                                                 |
|  <span data-ttu-id="d28cc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d28cc-107">Event Source</span></span>   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d28cc-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d28cc-108"> EDI</span></span>                                                      |
|    <span data-ttu-id="d28cc-109">元件</span><span class="sxs-lookup"><span data-stu-id="d28cc-109">Component</span></span>    |                                                                                            <span data-ttu-id="d28cc-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d28cc-110">EDI Engine</span></span>                                                                                            |
|  <span data-ttu-id="d28cc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d28cc-111">Symbolic Name</span></span>  |                                                                                                -                                                                                                 |
|  <span data-ttu-id="d28cc-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d28cc-112">Message Text</span></span>   | <span data-ttu-id="d28cc-113">處理傳送埠上的 Edifact 訊息時發生失敗{0}。</span><span class="sxs-lookup"><span data-stu-id="d28cc-113">A failure occurred in processing Edifact message on send port {0}.</span></span> <span data-ttu-id="d28cc-114">沒有協議的收件者及寄件者識別碼/辨識符號配對存在{1}， {2}， {3}， {4}。</span><span class="sxs-lookup"><span data-stu-id="d28cc-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span> <span data-ttu-id="d28cc-115">沒有合作對象有名稱{5}。</span><span class="sxs-lookup"><span data-stu-id="d28cc-115">No Party exists with name {5}.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="d28cc-116">說明</span><span class="sxs-lookup"><span data-stu-id="d28cc-116">Explanation</span></span>  
 <span data-ttu-id="d28cc-117">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析 EDIFACT 交換的合作對象，因為它無法符合升級傳送者辨識符號和識別項屬性，並提升接收者辨識符號和識別項使用合作對象的對應值的屬性。</span><span class="sxs-lookup"><span data-stu-id="d28cc-117">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because it was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d28cc-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d28cc-118">User Action</span></span>  
 <span data-ttu-id="d28cc-119">若要解決這個錯誤，請確定傳送者辨識符號和識別項 （UNB2.1 和 UNB2.2） 和接收者辨識符號和識別 （UNB3.1 和 UNB3.2） 在 [EDI 屬性] 對話方塊中的合作對象的 [UNB 區段定義] 頁面中定義符合對應交換的內容中的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="d28cc-119">To resolve this error, ensure that the sender qualifier and identifier (UNB2.1 and UNB2.2) and receiver qualifier and identifier (UNB3.1 and UNB3.2) defined in the party's UNB Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>