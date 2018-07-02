---
title: 處理傳送埠上的 Edifact 訊息時發生錯誤： 沒有合作對象名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 678baacb-1f21-4081-b788-ef346c3598ca
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 823b0d1315c82676017f0cc5e1bfa45b9ed9e342
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979335"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-party-with-name"></a><span data-ttu-id="543e7-102">處理傳送埠上的 Edifact 訊息時發生錯誤： 沒有合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="543e7-102">A failure occurred in processing Edifact message on send port: No Party with name</span></span>
## <a name="details"></a><span data-ttu-id="543e7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="543e7-103">Details</span></span>  
  
|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="543e7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="543e7-104">Product Name</span></span>   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| <span data-ttu-id="543e7-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="543e7-105">Product Version</span></span> |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    <span data-ttu-id="543e7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="543e7-106">Event ID</span></span>     |                                                 -                                                 |
|  <span data-ttu-id="543e7-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="543e7-107">Event Source</span></span>   |                                        <span data-ttu-id="543e7-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="543e7-108">BizTalk Server EDI</span></span>                                         |
|    <span data-ttu-id="543e7-109">元件</span><span class="sxs-lookup"><span data-stu-id="543e7-109">Component</span></span>    |                                            <span data-ttu-id="543e7-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="543e7-110">EDI Engine</span></span>                                             |
|  <span data-ttu-id="543e7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="543e7-111">Symbolic Name</span></span>  |                                                 -                                                 |
|  <span data-ttu-id="543e7-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="543e7-112">Message Text</span></span>   | <span data-ttu-id="543e7-113">處理傳送埠上的 Edifact 訊息時發生失敗{0}。</span><span class="sxs-lookup"><span data-stu-id="543e7-113">A failure occurred in processing Edifact message on send port {0}.</span></span> <span data-ttu-id="543e7-114">沒有合作對象有名稱{1}。</span><span class="sxs-lookup"><span data-stu-id="543e7-114">No Party exists with name {1}.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="543e7-115">說明</span><span class="sxs-lookup"><span data-stu-id="543e7-115">Explanation</span></span>  
 <span data-ttu-id="543e7-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 EDIFACT 交換，因為 BizTalk Server 無法比對與合作對象相關聯的傳送埠訂閱該交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="543e7-116">This Error/Warning/Information event indicates that BizTalk Server was unable to resolve the party for the EDIFACT interchange because BizTalk Server was unable to match the send port that subscribed to the interchange with the send port associated with a party.</span></span> <span data-ttu-id="543e7-117">會發生這種情況是如果沒有 [DestinationPartyName] 屬性，也不傳送者辨識符號和識別項以及接收者辨識符號和識別項屬性會升級，因此無法用於傳送端合作對象解析。</span><span class="sxs-lookup"><span data-stu-id="543e7-117">This occurs if neither the DestinationPartyName property nor the sender qualifier and identifier and receiver qualifier and identifier properties are promoted, so are unavailable for send-side party resolution.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="543e7-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="543e7-118">User Action</span></span>  
 <span data-ttu-id="543e7-119">若要解決這個錯誤，請確定傳送埠訂閱該交換的比對與合作對象關聯的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="543e7-119">To resolve this error, ensure that the send port that subscribed to the interchange matches the send port associated with a party.</span></span>