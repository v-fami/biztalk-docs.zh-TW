---
title: 未預期的根項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecccf57e-9295-4a6d-95b6-efec662478cf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0e54e0eac7e3f8ae54d23417033388bc493b0ab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981631"
---
# <a name="unexpected-root-element"></a><span data-ttu-id="60fc6-102">未預期的根項目</span><span class="sxs-lookup"><span data-stu-id="60fc6-102">Unexpected root element</span></span>
## <a name="details"></a><span data-ttu-id="60fc6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="60fc6-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="60fc6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="60fc6-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="60fc6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="60fc6-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="60fc6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="60fc6-106">Event ID</span></span>     |                                         <span data-ttu-id="60fc6-107">0</span><span class="sxs-lookup"><span data-stu-id="60fc6-107">0</span></span>                                          |
|  <span data-ttu-id="60fc6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="60fc6-108">Event Source</span></span>   |                                         <span data-ttu-id="60fc6-109">0</span><span class="sxs-lookup"><span data-stu-id="60fc6-109">0</span></span>                                          |
|    <span data-ttu-id="60fc6-110">元件</span><span class="sxs-lookup"><span data-stu-id="60fc6-110">Component</span></span>    |                                         <span data-ttu-id="60fc6-111">0</span><span class="sxs-lookup"><span data-stu-id="60fc6-111">0</span></span>                                          |
|  <span data-ttu-id="60fc6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="60fc6-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="60fc6-113">0</span><span class="sxs-lookup"><span data-stu-id="60fc6-113">0</span></span>                                          |
|  <span data-ttu-id="60fc6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="60fc6-114">Message Text</span></span>   |                              <span data-ttu-id="60fc6-115">未預期的根項目</span><span class="sxs-lookup"><span data-stu-id="60fc6-115">Unexpected root element</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="60fc6-116">說明</span><span class="sxs-lookup"><span data-stu-id="60fc6-116">Explanation</span></span>  
 <span data-ttu-id="60fc6-117">標頭屬性不是處於\<標頭\>...\</headers\>格式。</span><span class="sxs-lookup"><span data-stu-id="60fc6-117">Header property is not in \<headers\>….\</headers\> format.</span></span> <span data-ttu-id="60fc6-118">這種情況通常適用於 InboundHeaders 和 OutboundCustomHeaders。</span><span class="sxs-lookup"><span data-stu-id="60fc6-118">This situation normally applies to InboundHeaders and OutboundCustomHeaders.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="60fc6-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="60fc6-119">User Action</span></span>  
 <span data-ttu-id="60fc6-120">確保標頭屬性的格式\<標頭\>...\</headers\>。</span><span class="sxs-lookup"><span data-stu-id="60fc6-120">Ensure that header property is in the format of  \<headers\>…\</headers\>.</span></span>