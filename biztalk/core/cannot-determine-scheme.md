---
title: 無法判斷結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cc6e50b-33f5-4a88-b35d-075fdf8d79b2
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6086562f593b7ca04db63b7fb41f5cf128afe9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007167"
---
# <a name="cannot-determine-scheme"></a><span data-ttu-id="5059d-102">無法判斷配置</span><span class="sxs-lookup"><span data-stu-id="5059d-102">Cannot determine scheme</span></span>
## <a name="details"></a><span data-ttu-id="5059d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5059d-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="5059d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5059d-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="5059d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5059d-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="5059d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5059d-106">Event ID</span></span>     |                                         <span data-ttu-id="5059d-107">0</span><span class="sxs-lookup"><span data-stu-id="5059d-107">0</span></span>                                          |
|  <span data-ttu-id="5059d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="5059d-108">Event Source</span></span>   |                                         <span data-ttu-id="5059d-109">0</span><span class="sxs-lookup"><span data-stu-id="5059d-109">0</span></span>                                          |
|    <span data-ttu-id="5059d-110">元件</span><span class="sxs-lookup"><span data-stu-id="5059d-110">Component</span></span>    |                                         <span data-ttu-id="5059d-111">0</span><span class="sxs-lookup"><span data-stu-id="5059d-111">0</span></span>                                          |
|  <span data-ttu-id="5059d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5059d-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="5059d-113">0</span><span class="sxs-lookup"><span data-stu-id="5059d-113">0</span></span>                                          |
|  <span data-ttu-id="5059d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5059d-114">Message Text</span></span>   |                 <span data-ttu-id="5059d-115">無法判斷配置;請指定有效的繫結。</span><span class="sxs-lookup"><span data-stu-id="5059d-115">Cannot determine scheme; specify a valid binding.</span></span>                  |
  
## <a name="explanation"></a><span data-ttu-id="5059d-116">說明</span><span class="sxs-lookup"><span data-stu-id="5059d-116">Explanation</span></span>  
 <span data-ttu-id="5059d-117">已指定的傳輸繫結項目並沒有結構描述。</span><span class="sxs-lookup"><span data-stu-id="5059d-117">The transport binding element that has been specified does not have a scheme.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5059d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5059d-118">User Action</span></span>  
 <span data-ttu-id="5059d-119">選取有效的繫結，請確定傳輸繫結項目具有有效的配置。</span><span class="sxs-lookup"><span data-stu-id="5059d-119">Select a valid binding and make sure the transport binding element has a valid scheme.</span></span> <span data-ttu-id="5059d-120">如果使用自訂繫結，請確定已指定有效的傳輸繫結項目。</span><span class="sxs-lookup"><span data-stu-id="5059d-120">If using a custom binding, make sure a valid transport binding element is specified.</span></span>  
  
 <span data-ttu-id="5059d-121">如需詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="5059d-121">For additional information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="5059d-122">設定 WCF-Custom 配接器</span><span class="sxs-lookup"><span data-stu-id="5059d-122">Configuring the WCF-Custom Adapter</span></span>](../core/configuring-the-wcf-custom-adapter.md)