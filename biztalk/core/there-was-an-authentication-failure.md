---
title: 發生驗證失敗。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36524da9-da91-41e7-bf73-7781cde20c80
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5548d448d2c0d45addc72639ad229cf4ee1bf37f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022348"
---
# <a name="there-was-an-authentication-failure"></a><span data-ttu-id="88d1e-102">發生驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="88d1e-102">There was an authentication failure</span></span>
## <a name="details"></a><span data-ttu-id="88d1e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="88d1e-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="88d1e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="88d1e-104">Product Name</span></span>   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                         |
| <span data-ttu-id="88d1e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="88d1e-105">Product Version</span></span> |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                     |
|    <span data-ttu-id="88d1e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="88d1e-106">Event ID</span></span>     |                                                                                                 -                                                                                                 |
|  <span data-ttu-id="88d1e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="88d1e-107">Event Source</span></span>   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="88d1e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="88d1e-108"> EDI</span></span>                                                       |
|    <span data-ttu-id="88d1e-109">元件</span><span class="sxs-lookup"><span data-stu-id="88d1e-109">Component</span></span>    |                                                                                            <span data-ttu-id="88d1e-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="88d1e-110">EDI Engine</span></span>                                                                                             |
|  <span data-ttu-id="88d1e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="88d1e-111">Symbolic Name</span></span>  |                                                                                         <span data-ttu-id="88d1e-112">DescPartyNotFound</span><span class="sxs-lookup"><span data-stu-id="88d1e-112">DescPartyNotFound</span></span>                                                                                         |
|  <span data-ttu-id="88d1e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="88d1e-113">Message Text</span></span>   | <span data-ttu-id="88d1e-114">發生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="88d1e-114">There was an authentication failure.</span></span> <span data-ttu-id="88d1e-115">請確定正在處理的訊息比對合作對象存在。</span><span class="sxs-lookup"><span data-stu-id="88d1e-115">Make sure that a matching party exists for the message being processed.</span></span> <span data-ttu-id="88d1e-116">與訊息中的安全性/密碼資訊符合合作對象組態</span><span class="sxs-lookup"><span data-stu-id="88d1e-116">And the security/password information in the message matches the Party configuration</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="88d1e-117">說明</span><span class="sxs-lookup"><span data-stu-id="88d1e-117">Explanation</span></span>  
 <span data-ttu-id="88d1e-118">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為 BizTalk Server 無法驗證訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="88d1e-118">This Error/Warning/Information event indicates that the receive pipeline was unable to process the incoming interchange because BizTalk Server was unable to authenticate the sender of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="88d1e-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="88d1e-119">User Action</span></span>  
 <span data-ttu-id="88d1e-120">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="88d1e-120">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="88d1e-121">確認傳送者辨識符號和交換標頭 （欄位 ISA5 和 ISA6 為 X12 或 UNB2.1 和 UNB2.2，對於 EDIFACT） 中的識別項相符的傳送者辨識符號和識別項 （如 [交換處理屬性] 頁面中所定義的合作對象屬性中[EDI 屬性] 對話方塊）。</span><span class="sxs-lookup"><span data-stu-id="88d1e-121">Verify that the sender qualifier and identifier in the interchange header (fields ISA5 and ISA6 for X12 or UNB2.1 and UNB2.2 for EDIFACT) match the sender qualifier and identifier in the properties of a party (as defined in the Interchange Processing Properties page of the EDI Properties dialog box).</span></span>  
  
-   <span data-ttu-id="88d1e-122">確認交換標頭中的安全性/密碼資訊 (在 X12 中為 [ISA3] 和 [ISA4] 欄位；在 EDIFACT 中為 [UNB6.1] 和 [UNB6.2] 欄位) 和合作對象屬性中的安全性/密碼資訊 (如 [EDI 屬性] 對話方塊 [交換處理屬性] 頁面中定義的內容) 相符。</span><span class="sxs-lookup"><span data-stu-id="88d1e-122">Verify that the security/password information in the header of the interchange (fields ISA3 and ISA4 for X12 or UNB6.1 and UNB6.2 for EDIFACT) match the security/password information in the properties of a party (as defined in the Interchange Processing Properties page of the EDI Properties dialog box).</span></span>