---
title: "BizTalk 訊息內文元素未指定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5d63c0-af96-4e34-828f-d29638cdf46d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf79c8896169a06df66a8484377816c9897531e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-message-body-element-not-specified"></a><span data-ttu-id="912d4-102">未指定 BizTalk 訊息內文元素</span><span class="sxs-lookup"><span data-stu-id="912d4-102">BizTalk message body element not specified</span></span>
## <a name="details"></a><span data-ttu-id="912d4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="912d4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="912d4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="912d4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="912d4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="912d4-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="912d4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="912d4-106">Event ID</span></span>|<span data-ttu-id="912d4-107">0</span><span class="sxs-lookup"><span data-stu-id="912d4-107">0</span></span>|  
|<span data-ttu-id="912d4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="912d4-108">Event Source</span></span>|<span data-ttu-id="912d4-109">0</span><span class="sxs-lookup"><span data-stu-id="912d4-109">0</span></span>|  
|<span data-ttu-id="912d4-110">元件</span><span class="sxs-lookup"><span data-stu-id="912d4-110">Component</span></span>|<span data-ttu-id="912d4-111">0</span><span class="sxs-lookup"><span data-stu-id="912d4-111">0</span></span>|  
|<span data-ttu-id="912d4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="912d4-112">Symbolic Name</span></span>|<span data-ttu-id="912d4-113">0</span><span class="sxs-lookup"><span data-stu-id="912d4-113">0</span></span>|  
|<span data-ttu-id="912d4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="912d4-114">Message Text</span></span>|<span data-ttu-id="912d4-115">未指定 BizTalk 訊息內文元素</span><span class="sxs-lookup"><span data-stu-id="912d4-115">BizTalk message body element not specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="912d4-116">說明</span><span class="sxs-lookup"><span data-stu-id="912d4-116">Explanation</span></span>  
 <span data-ttu-id="912d4-117">此錯誤表示使用了輸出 WCF 訊息的範本選項。</span><span class="sxs-lookup"><span data-stu-id="912d4-117">This error indicates the use of the template option for the outbound WCF message.</span></span> <span data-ttu-id="912d4-118">但範本運算式不包含 BizTalk 訊息內文元素。</span><span class="sxs-lookup"><span data-stu-id="912d4-118">However, the template expression doesn’t contain the BizTalk message body element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="912d4-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="912d4-119">User Action</span></span>  
 <span data-ttu-id="912d4-120">請確認範本運算式包含下列項目： \< **bts 訊息主體 xmlns ="http://www.microsoft.com/schemas/bts2007"encoding ="[xml &#124; base64 &#124; 十六進位 &#124; 字串]"/**>。</span><span class="sxs-lookup"><span data-stu-id="912d4-120">Ensure that the template expression contains the following element: \<**bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="[xml&#124;base64&#124;hex&#124;string]"/**>.</span></span>