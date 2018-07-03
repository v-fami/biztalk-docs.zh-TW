---
title: 此 AS2 交換的合作對象必須包含值的 AS2-從 |Microsoft Docs
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
ms.openlocfilehash: 637224e0519a181c71b12e390c39c821ad354ac6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009247"
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-from"></a><span data-ttu-id="27337-102">此 AS2 交換的合作對象必須包含 AS2-From 的值</span><span class="sxs-lookup"><span data-stu-id="27337-102">The party for this AS2 interchange must contain a value for AS2-From</span></span>
## <a name="details"></a><span data-ttu-id="27337-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="27337-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="27337-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="27337-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="27337-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="27337-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="27337-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="27337-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="27337-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="27337-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="27337-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="27337-108"> EDI</span></span> |
|    <span data-ttu-id="27337-109">元件</span><span class="sxs-lookup"><span data-stu-id="27337-109">Component</span></span>    |                                       <span data-ttu-id="27337-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="27337-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="27337-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="27337-111">Symbolic Name</span></span>  |                              <span data-ttu-id="27337-112">InvalidAgreementAS2FromName</span><span class="sxs-lookup"><span data-stu-id="27337-112">InvalidAgreementAS2FromName</span></span>                               |
|  <span data-ttu-id="27337-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="27337-113">Message Text</span></span>   |         <span data-ttu-id="27337-114">此 AS2 交換的合作對象必須包含 AS2-From 的值。</span><span class="sxs-lookup"><span data-stu-id="27337-114">The party for this AS2 interchange must contain a value for AS2-From.</span></span>          |
  
## <a name="explanation"></a><span data-ttu-id="27337-115">說明</span><span class="sxs-lookup"><span data-stu-id="27337-115">Explanation</span></span>  
 <span data-ttu-id="27337-116">這個錯誤/警告/資訊事件表示，傳送管線無法傳送 AS2 訊息，因為 AS2-從屬性未設定已解析合作對象做為訊息接收者。</span><span class="sxs-lookup"><span data-stu-id="27337-116">This Error/Warning/Information event indicates that the send pipeline could not send the AS2 message because the AS2-From property was not set for the resolved party as message receiver.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="27337-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="27337-117">User Action</span></span>  
 <span data-ttu-id="27337-118">若要解決這個錯誤，開啟 BizTalk Server 管理主控台、 移至合作對象節點中，開啟 [AS2 屬性] 對話方塊中的訊息，來解析合作對象按一下合作對象當做 AS2 訊息接收者] 節點中，然後輸入 [AS2 的值-屬性。</span><span class="sxs-lookup"><span data-stu-id="27337-118">To resolve this error, open the BizTalk Server Administration Console, move to the Parties node, open the AS2 Properties dialog box for the party resolved for the message, click the Party as AS2 Message Receiver node, and then enter a value for the AS2-From property.</span></span>