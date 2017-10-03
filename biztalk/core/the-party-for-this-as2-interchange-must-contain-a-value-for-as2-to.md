---
title: "此 AS2 交換的合作對象 AS2 必須包含值-至 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 029eae5d-4c13-402d-90c5-8e9ef3814a1f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adda90c2ae0e5dfa659e3bd36dcadfc58f815ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-to"></a><span data-ttu-id="179aa-102">此 AS2 交換的合作對象 AS2 必須包含值-至</span><span class="sxs-lookup"><span data-stu-id="179aa-102">The party for this AS2 interchange must contain a value for AS2-To</span></span>
## <a name="details"></a><span data-ttu-id="179aa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="179aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="179aa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="179aa-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="179aa-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="179aa-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="179aa-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="179aa-106">Event ID</span></span>|-|  
|<span data-ttu-id="179aa-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="179aa-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="179aa-108">EDI</span><span class="sxs-lookup"><span data-stu-id="179aa-108"> EDI</span></span>|  
|<span data-ttu-id="179aa-109">元件</span><span class="sxs-lookup"><span data-stu-id="179aa-109">Component</span></span>|<span data-ttu-id="179aa-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="179aa-110">AS2 Engine</span></span>|  
|<span data-ttu-id="179aa-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="179aa-111">Symbolic Name</span></span>|<span data-ttu-id="179aa-112">InvalidAgreementAS2ToName</span><span class="sxs-lookup"><span data-stu-id="179aa-112">InvalidAgreementAS2ToName</span></span>|  
|<span data-ttu-id="179aa-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="179aa-113">Message Text</span></span>|<span data-ttu-id="179aa-114">此 AS2 交換的合作對象必須包含 AS2-To 的值。</span><span class="sxs-lookup"><span data-stu-id="179aa-114">The party for this AS2 interchange must contain a value for AS2-To.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="179aa-115">說明</span><span class="sxs-lookup"><span data-stu-id="179aa-115">Explanation</span></span>  
 <span data-ttu-id="179aa-116">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄 AS2 訊息因為 AS2-屬性未設定已解析合作對象做為訊息接收者。</span><span class="sxs-lookup"><span data-stu-id="179aa-116">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing AS2 message because the AS2-To property was not set for the resolved party as message receiver.</span></span> <span data-ttu-id="179aa-117">這表示外寄 AS2 訊息的合作對象已解析藉由比對訂閱訊息的傳送埠的合作對象相關聯的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="179aa-117">This indicates that the party for the outgoing AS2 message was resolved by matching the send port associated with the party with the send port that subscribed to the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="179aa-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="179aa-118">User Action</span></span>  
 <span data-ttu-id="179aa-119">若要解決這個錯誤，執行作業，如下所示：</span><span class="sxs-lookup"><span data-stu-id="179aa-119">To resolve this error, do as follows:</span></span>  
  
1.  <span data-ttu-id="179aa-120">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="179aa-120">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="179aa-121">移至 [合作對象] 節點，然後開啟 [AS2 屬性] 對話方塊的合作對象解析訊息。</span><span class="sxs-lookup"><span data-stu-id="179aa-121">Move to the Parties node, and open the AS2 Properties dialog box for the party resolved for the message.</span></span>  
  
3.  <span data-ttu-id="179aa-122">您可以按一下 合作對象做為 AS2 訊息接收者的節點。</span><span class="sxs-lookup"><span data-stu-id="179aa-122">Click the Party as AS2 Message Receiver node.</span></span>  
  
4.  <span data-ttu-id="179aa-123">輸入 AS2 的值-屬性。</span><span class="sxs-lookup"><span data-stu-id="179aa-123">Enter a value for the AS2-To property.</span></span>