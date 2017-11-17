---
title: "無法存取使用接收者識別的協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 470325f4-abc4-40bb-9109-9ffc73b496df
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f41b126ca0ebb96716f21381d2e1681ea59bd414
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-agreement-using-receiver-identity"></a><span data-ttu-id="01726-102">無法存取使用接收者識別的協議</span><span class="sxs-lookup"><span data-stu-id="01726-102">Unable to access agreement using receiver identity</span></span>
## <a name="details"></a><span data-ttu-id="01726-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="01726-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01726-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="01726-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="01726-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="01726-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="01726-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="01726-106">Event ID</span></span>|-|  
|<span data-ttu-id="01726-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="01726-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="01726-108">EDI</span><span class="sxs-lookup"><span data-stu-id="01726-108"> EDI</span></span>|  
|<span data-ttu-id="01726-109">元件</span><span class="sxs-lookup"><span data-stu-id="01726-109">Component</span></span>|<span data-ttu-id="01726-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="01726-110">AS2 Engine</span></span>|  
|<span data-ttu-id="01726-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="01726-111">Symbolic Name</span></span>|<span data-ttu-id="01726-112">UnableToLocateAS2PartyByPartyNameError</span><span class="sxs-lookup"><span data-stu-id="01726-112">UnableToLocateAS2PartyByPartyNameError</span></span>|  
|<span data-ttu-id="01726-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="01726-113">Message Text</span></span>|<span data-ttu-id="01726-114">無法存取使用接收者識別的協議： {0}</span><span class="sxs-lookup"><span data-stu-id="01726-114">Unable to access agreement using receiver identity: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="01726-115">說明</span><span class="sxs-lookup"><span data-stu-id="01726-115">Explanation</span></span>  
 <span data-ttu-id="01726-116">此錯誤表示，傳送管線無法判斷外寄 AS2 訊息的合作對象因為它無法符合外寄訊息的 AS2To 內容屬性或 Http.UserHttpHeaders 內容屬性的名稱中的 AS2To 屬性在 AS2 合作對象的合作對象當做 AS2 訊息接收者頁面的 [AS2 屬性] 對話方塊中的屬性。</span><span class="sxs-lookup"><span data-stu-id="01726-116">This error indicates that the send pipeline could not determine the party for an outgoing AS2 message because it could not match the AS2To context property of the outbound message or the AS2To property in the Http.UserHttpHeaders context property with the name of the party in the AS2-To property in the Party as AS2 Message Receiver page of the AS2 Properties dialog box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="01726-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="01726-117">User Action</span></span>  
 <span data-ttu-id="01726-118">若要解決這個錯誤，請設定 AS2-合作對象當做 AS2 訊息接收者頁面錯誤的 AS2 訊息相關聯的適當的合作對象名稱 AS2 屬性 對話方塊中的屬性。</span><span class="sxs-lookup"><span data-stu-id="01726-118">To resolve this error, set the AS2-To property in the Party as AS2 Message Receiver page of the AS2 Properties dialog box to the appropriate party name associated with the AS2 message that is in error.</span></span>