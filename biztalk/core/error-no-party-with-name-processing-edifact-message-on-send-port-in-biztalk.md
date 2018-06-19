---
title: 在處理傳送埠上的 Edifact 訊息發生失敗： 沒有合作對象名稱 |Microsoft 文件
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
ms.openlocfilehash: 6becad3fefaa8167c9cf1af051731aa08be0d80a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005151"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-party-with-name"></a><span data-ttu-id="097bb-102">在處理傳送埠上的 Edifact 訊息發生失敗： 沒有合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="097bb-102">A failure occurred in processing Edifact message on send port: No Party with name</span></span>
## <a name="details"></a><span data-ttu-id="097bb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="097bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="097bb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="097bb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="097bb-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="097bb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="097bb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="097bb-106">Event ID</span></span>|-|  
|<span data-ttu-id="097bb-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="097bb-107">Event Source</span></span>|<span data-ttu-id="097bb-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="097bb-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="097bb-109">元件</span><span class="sxs-lookup"><span data-stu-id="097bb-109">Component</span></span>|<span data-ttu-id="097bb-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="097bb-110">EDI Engine</span></span>|  
|<span data-ttu-id="097bb-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="097bb-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="097bb-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="097bb-112">Message Text</span></span>|<span data-ttu-id="097bb-113">在處理傳送埠 {0} 上的 Edifact 訊息發生失敗。</span><span class="sxs-lookup"><span data-stu-id="097bb-113">A failure occurred in processing Edifact message on send port {0}.</span></span> <span data-ttu-id="097bb-114">沒有合作對象名稱 {1} 存在。</span><span class="sxs-lookup"><span data-stu-id="097bb-114">No Party exists with name {1}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="097bb-115">說明</span><span class="sxs-lookup"><span data-stu-id="097bb-115">Explanation</span></span>  
 <span data-ttu-id="097bb-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析 EDIFACT 交換的合作對象，因為 BizTalk Server 無法比對與合作對象相關聯的傳送埠訂閱該交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="097bb-116">This Error/Warning/Information event indicates that BizTalk Server was unable to resolve the party for the EDIFACT interchange because BizTalk Server was unable to match the send port that subscribed to the interchange with the send port associated with a party.</span></span> <span data-ttu-id="097bb-117">會發生這種情況是如果不 DestinationPartyName 屬性、 傳送者辨識符號和識別項以及接收者辨識符號和識別項屬性會升級，因此無法用於傳送端合作對象解析。</span><span class="sxs-lookup"><span data-stu-id="097bb-117">This occurs if neither the DestinationPartyName property nor the sender qualifier and identifier and receiver qualifier and identifier properties are promoted, so are unavailable for send-side party resolution.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="097bb-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="097bb-118">User Action</span></span>  
 <span data-ttu-id="097bb-119">若要解決這個錯誤，請訂閱該交換的傳送埠比對與合作對象關聯的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="097bb-119">To resolve this error, ensure that the send port that subscribed to the interchange matches the send port associated with a party.</span></span>