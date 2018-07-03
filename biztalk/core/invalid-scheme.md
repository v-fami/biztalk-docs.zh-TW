---
title: 無效的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bb3e70a-d23c-45e9-bde5-edae6731e58a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 063c60ed07d89429f14f7ed3b7c090cdc0bac033
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008159"
---
# <a name="invalid-scheme"></a><span data-ttu-id="700d6-102">無效的結構描述</span><span class="sxs-lookup"><span data-stu-id="700d6-102">Invalid scheme</span></span>
## <a name="details"></a><span data-ttu-id="700d6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="700d6-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="700d6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="700d6-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="700d6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="700d6-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="700d6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="700d6-106">Event ID</span></span>     |                                         <span data-ttu-id="700d6-107">0</span><span class="sxs-lookup"><span data-stu-id="700d6-107">0</span></span>                                          |
|  <span data-ttu-id="700d6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="700d6-108">Event Source</span></span>   |                                         <span data-ttu-id="700d6-109">0</span><span class="sxs-lookup"><span data-stu-id="700d6-109">0</span></span>                                          |
|    <span data-ttu-id="700d6-110">元件</span><span class="sxs-lookup"><span data-stu-id="700d6-110">Component</span></span>    |                                         <span data-ttu-id="700d6-111">0</span><span class="sxs-lookup"><span data-stu-id="700d6-111">0</span></span>                                          |
|  <span data-ttu-id="700d6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="700d6-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="700d6-113">0</span><span class="sxs-lookup"><span data-stu-id="700d6-113">0</span></span>                                          |
|  <span data-ttu-id="700d6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="700d6-114">Message Text</span></span>   |                  <span data-ttu-id="700d6-115">無效的結構描述;必須是配置 」{0}「 或 」{1}"</span><span class="sxs-lookup"><span data-stu-id="700d6-115">Invalid scheme; expecting scheme "{0}" or "{1}"</span></span>                   |
  
## <a name="explanation"></a><span data-ttu-id="700d6-116">說明</span><span class="sxs-lookup"><span data-stu-id="700d6-116">Explanation</span></span>  
 <span data-ttu-id="700d6-117">其中一個下列的情況下發生： 統一資源識別元 （URI) 欄位中指定的位址必須以 http:// 或 https:// 開頭。</span><span class="sxs-lookup"><span data-stu-id="700d6-117">One of the following situations has occurred: the address that is specified in the URI (uniform resource identifier) field must start with either http:// or https://.</span></span> <span data-ttu-id="700d6-118">或者配置不符合傳輸繫結元素的實作中指定的規格。</span><span class="sxs-lookup"><span data-stu-id="700d6-118">Or the scheme does not match what is specified in the implementation of the transport binding element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="700d6-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="700d6-119">User Action</span></span>  
 <span data-ttu-id="700d6-120">輸入有效的 proxy 位址以 http:// 或 https:// 開頭的 URI</span><span class="sxs-lookup"><span data-stu-id="700d6-120">Enter a valid proxy address URI that starts with http:// or https://</span></span>