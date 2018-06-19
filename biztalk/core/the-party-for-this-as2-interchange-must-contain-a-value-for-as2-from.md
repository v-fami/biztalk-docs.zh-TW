---
title: 此 AS2 交換的合作對象 AS2 必須包含值-從 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d338759-5646-4dc2-8319-a42aaa8c3d9c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b52f153cce06eac014d98fa1908978694fc67706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278774"
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-from"></a><span data-ttu-id="e1ee2-102">此 AS2 交換的合作對象必須包含 AS2-From 的值</span><span class="sxs-lookup"><span data-stu-id="e1ee2-102">The party for this AS2 interchange must contain a value for AS2-From</span></span>
## <a name="details"></a><span data-ttu-id="e1ee2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1ee2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1ee2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e1ee2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e1ee2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e1ee2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e1ee2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e1ee2-106">Event ID</span></span>|-|  
|<span data-ttu-id="e1ee2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e1ee2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e1ee2-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e1ee2-108"> EDI</span></span>|  
|<span data-ttu-id="e1ee2-109">元件</span><span class="sxs-lookup"><span data-stu-id="e1ee2-109">Component</span></span>|<span data-ttu-id="e1ee2-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="e1ee2-110">AS2 Engine</span></span>|  
|<span data-ttu-id="e1ee2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e1ee2-111">Symbolic Name</span></span>|<span data-ttu-id="e1ee2-112">InvalidAgreementAS2FromName</span><span class="sxs-lookup"><span data-stu-id="e1ee2-112">InvalidAgreementAS2FromName</span></span>|  
|<span data-ttu-id="e1ee2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e1ee2-113">Message Text</span></span>|<span data-ttu-id="e1ee2-114">此 AS2 交換的合作對象必須包含 AS2-From 的值。</span><span class="sxs-lookup"><span data-stu-id="e1ee2-114">The party for this AS2 interchange must contain a value for AS2-From.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1ee2-115">說明</span><span class="sxs-lookup"><span data-stu-id="e1ee2-115">Explanation</span></span>  
 <span data-ttu-id="e1ee2-116">這個錯誤/警告/資訊事件表示，傳送管線無法傳送 AS2 訊息，因為 AS2-從屬性未設定已解析合作對象做為訊息接收者。</span><span class="sxs-lookup"><span data-stu-id="e1ee2-116">This Error/Warning/Information event indicates that the send pipeline could not send the AS2 message because the AS2-From property was not set for the resolved party as message receiver.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1ee2-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e1ee2-117">User Action</span></span>  
 <span data-ttu-id="e1ee2-118">若要解決這個錯誤，開啟 BizTalk Server 管理主控台，移至合作對象節點中，開啟 AS2 屬性 對話方塊的 合作對象解析訊息時，按一下合作對象當做 AS2 訊息接收者節點，然後輸入 AS2 的值-屬性。</span><span class="sxs-lookup"><span data-stu-id="e1ee2-118">To resolve this error, open the BizTalk Server Administration Console, move to the Parties node, open the AS2 Properties dialog box for the party resolved for the message, click the Party as AS2 Message Receiver node, and then enter a value for the AS2-From property.</span></span>