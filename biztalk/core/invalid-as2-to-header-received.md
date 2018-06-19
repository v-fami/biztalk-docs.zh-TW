---
title: 無效的 AS2-To 收到的標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56cd16b3-511b-4716-8806-817f174f0b0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 750166045224754c05e4345c2e57e16950b89c9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256998"
---
# <a name="invalid-as2-to-header-received"></a><span data-ttu-id="484e2-102">無效的 AS2-To 收到的標頭</span><span class="sxs-lookup"><span data-stu-id="484e2-102">Invalid AS2-To header received</span></span>
## <a name="details"></a><span data-ttu-id="484e2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="484e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="484e2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="484e2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="484e2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="484e2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="484e2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="484e2-106">Event ID</span></span>|-|  
|<span data-ttu-id="484e2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="484e2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="484e2-108">EDI</span><span class="sxs-lookup"><span data-stu-id="484e2-108"> EDI</span></span>|  
|<span data-ttu-id="484e2-109">元件</span><span class="sxs-lookup"><span data-stu-id="484e2-109">Component</span></span>|<span data-ttu-id="484e2-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="484e2-110">AS2 Engine</span></span>|  
|<span data-ttu-id="484e2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="484e2-111">Symbolic Name</span></span>|<span data-ttu-id="484e2-112">InvalidAS2ToNameHeaderReceivedError</span><span class="sxs-lookup"><span data-stu-id="484e2-112">InvalidAS2ToNameHeaderReceivedError</span></span>|  
|<span data-ttu-id="484e2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="484e2-113">Message Text</span></span>|<span data-ttu-id="484e2-114">收到無效的 AS2-To 標頭。</span><span class="sxs-lookup"><span data-stu-id="484e2-114">Invalid AS2-To header received.</span></span>  <span data-ttu-id="484e2-115">值： {0}</span><span class="sxs-lookup"><span data-stu-id="484e2-115">Value: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="484e2-116">說明</span><span class="sxs-lookup"><span data-stu-id="484e2-116">Explanation</span></span>  
 <span data-ttu-id="484e2-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為值的 AS2-To 標頭訊息中不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="484e2-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-To header in the message did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="484e2-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="484e2-118">User Action</span></span>  
 <span data-ttu-id="484e2-119">若要解決這個錯誤，請確定 AS2 中的值-給訊息標頭符合 AS2 RFC 4130 第 6.2 節的規格。</span><span class="sxs-lookup"><span data-stu-id="484e2-119">To resolve this error, make sure that the value in the AS2-To header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>