---
title: "無效的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb3e70a-d23c-45e9-bde5-edae6731e58a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5736a3738a9598f4c4b419d7e291c3c3e32207f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-scheme"></a><span data-ttu-id="210f8-102">無效的結構描述</span><span class="sxs-lookup"><span data-stu-id="210f8-102">Invalid scheme</span></span>
## <a name="details"></a><span data-ttu-id="210f8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="210f8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="210f8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="210f8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="210f8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="210f8-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="210f8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="210f8-106">Event ID</span></span>|<span data-ttu-id="210f8-107">0</span><span class="sxs-lookup"><span data-stu-id="210f8-107">0</span></span>|  
|<span data-ttu-id="210f8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="210f8-108">Event Source</span></span>|<span data-ttu-id="210f8-109">0</span><span class="sxs-lookup"><span data-stu-id="210f8-109">0</span></span>|  
|<span data-ttu-id="210f8-110">元件</span><span class="sxs-lookup"><span data-stu-id="210f8-110">Component</span></span>|<span data-ttu-id="210f8-111">0</span><span class="sxs-lookup"><span data-stu-id="210f8-111">0</span></span>|  
|<span data-ttu-id="210f8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="210f8-112">Symbolic Name</span></span>|<span data-ttu-id="210f8-113">0</span><span class="sxs-lookup"><span data-stu-id="210f8-113">0</span></span>|  
|<span data-ttu-id="210f8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="210f8-114">Message Text</span></span>|<span data-ttu-id="210f8-115">無效的結構描述。必須是配置"{0}"或"{1}"</span><span class="sxs-lookup"><span data-stu-id="210f8-115">Invalid scheme; expecting scheme "{0}" or "{1}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="210f8-116">說明</span><span class="sxs-lookup"><span data-stu-id="210f8-116">Explanation</span></span>  
 <span data-ttu-id="210f8-117">發生下列情況下其中一項： 指定的 URI （統一資源識別項） 欄位中的位址必須以 http:// 或 https:// 開頭。</span><span class="sxs-lookup"><span data-stu-id="210f8-117">One of the following situations has occurred: the address that is specified in the URI (uniform resource identifier) field must start with either http:// or https://.</span></span> <span data-ttu-id="210f8-118">或者配置不符合傳輸繫結元素的實作中指定的規格。</span><span class="sxs-lookup"><span data-stu-id="210f8-118">Or the scheme does not match what is specified in the implementation of the transport binding element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="210f8-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="210f8-119">User Action</span></span>  
 <span data-ttu-id="210f8-120">輸入有效的 proxy 位址以 http:// 或 https:// 開頭的 URI</span><span class="sxs-lookup"><span data-stu-id="210f8-120">Enter a valid proxy address URI that starts with http:// or https://</span></span>