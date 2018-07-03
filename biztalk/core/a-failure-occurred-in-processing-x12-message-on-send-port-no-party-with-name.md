---
title: 失敗發生在處理 X12 訊息在傳送埠： 沒有合作對象名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af059a04-3b7c-48e2-a3bf-48ad62deb139
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 817840dae0db408d4f78732f5d470605a05edf71
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014791"
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-party-with-name"></a><span data-ttu-id="94671-102">處理傳送埠上的 X12 訊息時發生失敗：沒有名稱的合作對象</span><span class="sxs-lookup"><span data-stu-id="94671-102">A failure occurred in processing X12 message on send port: No Party with name</span></span>
## <a name="details"></a><span data-ttu-id="94671-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="94671-103">Details</span></span>  
  
|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
|  <span data-ttu-id="94671-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="94671-104">Product Name</span></span>   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| <span data-ttu-id="94671-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="94671-105">Product Version</span></span> |                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                   |
|    <span data-ttu-id="94671-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="94671-106">Event ID</span></span>     |                                               -                                               |
|  <span data-ttu-id="94671-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="94671-107">Event Source</span></span>   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="94671-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="94671-108"> EDI</span></span>     |
|    <span data-ttu-id="94671-109">元件</span><span class="sxs-lookup"><span data-stu-id="94671-109">Component</span></span>    |                                          <span data-ttu-id="94671-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="94671-110">EDI Engine</span></span>                                           |
|  <span data-ttu-id="94671-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="94671-111">Symbolic Name</span></span>  |                                               -                                               |
|  <span data-ttu-id="94671-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="94671-112">Message Text</span></span>   | <span data-ttu-id="94671-113">失敗發生在處理 X12 訊息傳送埠上的{0}。</span><span class="sxs-lookup"><span data-stu-id="94671-113">A failure occurred in processing X12 message on send port {0}.</span></span> <span data-ttu-id="94671-114">沒有合作對象有名稱{1}。</span><span class="sxs-lookup"><span data-stu-id="94671-114">No Party exists with name {1}.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="94671-115">說明</span><span class="sxs-lookup"><span data-stu-id="94671-115">Explanation</span></span>  
 <span data-ttu-id="94671-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 X12 交換，因為 BizTalk Server 無法比對與合作對象相關聯的傳送埠訂閱該交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="94671-116">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the X12 interchange because BizTalk Server was unable to match the send port that subscribed to the interchange with the send port associated with a party.</span></span> <span data-ttu-id="94671-117">會發生這種情況是如果沒有 [DestinationPartyName] 屬性中，或傳送者辨識符號、 寄件者識別碼、 接收者辨識符號和接收者識別項屬性，會升級，因此無法用於傳送端合作對象解析。</span><span class="sxs-lookup"><span data-stu-id="94671-117">This occurs if neither the DestinationPartyName property, nor the sender qualifier, sender identifier, receiver qualifier, and receiver identifier properties, are promoted, so are unavailable for send-side party resolution.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94671-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="94671-118">User Action</span></span>  
 <span data-ttu-id="94671-119">若要解決這個錯誤，請確定傳送埠訂閱該交換的比對與合作對象關聯的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="94671-119">To resolve this error, ensure the send port that subscribed to the interchange matches the send port associated with a party.</span></span>