---
title: 無法從驗證地址的繫結取得配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b002084a-63ae-4685-8ce3-88cc6489e19e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2032decfdf59ae175f3ee8fc686341c8a4061fc6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991335"
---
# <a name="cannot-obtain-scheme-from-binding-to-validate-address"></a><span data-ttu-id="bc3e9-102">無法取得配置來驗證地址的繫結</span><span class="sxs-lookup"><span data-stu-id="bc3e9-102">Cannot obtain scheme from binding to validate address</span></span>
## <a name="details"></a><span data-ttu-id="bc3e9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bc3e9-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="bc3e9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bc3e9-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="bc3e9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bc3e9-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="bc3e9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bc3e9-106">Event ID</span></span>     |                                         <span data-ttu-id="bc3e9-107">0</span><span class="sxs-lookup"><span data-stu-id="bc3e9-107">0</span></span>                                          |
|  <span data-ttu-id="bc3e9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bc3e9-108">Event Source</span></span>   |                                         <span data-ttu-id="bc3e9-109">0</span><span class="sxs-lookup"><span data-stu-id="bc3e9-109">0</span></span>                                          |
|    <span data-ttu-id="bc3e9-110">元件</span><span class="sxs-lookup"><span data-stu-id="bc3e9-110">Component</span></span>    |                                         <span data-ttu-id="bc3e9-111">0</span><span class="sxs-lookup"><span data-stu-id="bc3e9-111">0</span></span>                                          |
|  <span data-ttu-id="bc3e9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bc3e9-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="bc3e9-113">0</span><span class="sxs-lookup"><span data-stu-id="bc3e9-113">0</span></span>                                          |
|  <span data-ttu-id="bc3e9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bc3e9-114">Message Text</span></span>   |               <span data-ttu-id="bc3e9-115">無法取得配置來驗證地址的繫結。</span><span class="sxs-lookup"><span data-stu-id="bc3e9-115">Cannot obtain scheme from binding to validate address.</span></span>               |
  
## <a name="explanation"></a><span data-ttu-id="bc3e9-116">說明</span><span class="sxs-lookup"><span data-stu-id="bc3e9-116">Explanation</span></span>  
 <span data-ttu-id="bc3e9-117">已指定的傳輸繫結項目並沒有結構描述。</span><span class="sxs-lookup"><span data-stu-id="bc3e9-117">The transport binding element that has been specified does not have a scheme.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bc3e9-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bc3e9-118">User Action</span></span>  
 <span data-ttu-id="bc3e9-119">請確定傳輸繫結項目具有有效的配置，或已選取有效的傳輸繫結項目。</span><span class="sxs-lookup"><span data-stu-id="bc3e9-119">Make sure that the transport binding element has a valid scheme, or that a valid transport binding element is selected.</span></span> <span data-ttu-id="bc3e9-120">如果使用自訂繫結，請確定已指定有效的傳輸繫結項目。</span><span class="sxs-lookup"><span data-stu-id="bc3e9-120">If using a custom binding, make sure a valid transport binding element is specified.</span></span>  
  
 <span data-ttu-id="bc3e9-121">如需詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="bc3e9-121">For additional information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="bc3e9-122">設定 WCF-Custom 配接器</span><span class="sxs-lookup"><span data-stu-id="bc3e9-122">Configuring the WCF-Custom Adapter</span></span>](../core/configuring-the-wcf-custom-adapter.md)