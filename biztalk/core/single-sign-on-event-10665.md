---
title: 單一登入： 事件 10665 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d0de9d0-9b46-4f3a-b796-1ce3de01cf4c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e820b5d682a3ea5947d4811038d4a9bc5eaa38c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013919"
---
# <a name="single-sign-on-event-10665"></a><span data-ttu-id="35a81-102">單一登入： 事件 10665</span><span class="sxs-lookup"><span data-stu-id="35a81-102">Single Sign-On: Event 10665</span></span>
## <a name="details"></a><span data-ttu-id="35a81-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="35a81-103">Details</span></span>  

|                 |                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="35a81-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="35a81-104">Product Name</span></span>   |                                               <span data-ttu-id="35a81-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="35a81-105">Enterprise Single Sign-On</span></span>                                                |
| <span data-ttu-id="35a81-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="35a81-106">Product Version</span></span> |                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                               |
|    <span data-ttu-id="35a81-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="35a81-107">Event ID</span></span>     |                                                         <span data-ttu-id="35a81-108">10665</span><span class="sxs-lookup"><span data-stu-id="35a81-108">10665</span></span>                                                          |
|  <span data-ttu-id="35a81-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="35a81-109">Event Source</span></span>   |                                                         <span data-ttu-id="35a81-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="35a81-110">ENTSSO</span></span>                                                         |
|    <span data-ttu-id="35a81-111">元件</span><span class="sxs-lookup"><span data-stu-id="35a81-111">Component</span></span>    |                                                          <span data-ttu-id="35a81-112">N\A</span><span class="sxs-lookup"><span data-stu-id="35a81-112">N\A</span></span>                                                           |
|  <span data-ttu-id="35a81-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="35a81-113">Symbolic Name</span></span>  |                                                 <span data-ttu-id="35a81-114">SSO_WARN_NO_PROPERTIES</span><span class="sxs-lookup"><span data-stu-id="35a81-114">SSO_WARN_NO_PROPERTIES</span></span>                                                 |
|  <span data-ttu-id="35a81-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="35a81-115">Message Text</span></span>   | <span data-ttu-id="35a81-116">讀取密碼同步配接器屬性時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="35a81-116">Error reading password sync adapter properties.</span></span> <span data-ttu-id="35a81-117">使用 defaults.%r</span><span class="sxs-lookup"><span data-stu-id="35a81-117">Using defaults.%r</span></span><br /><br /> <span data-ttu-id="35a81-118">配接器: %1 %r</span><span class="sxs-lookup"><span data-stu-id="35a81-118">Adapter: %1%r</span></span><br /><br /> <span data-ttu-id="35a81-119">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="35a81-119">Error Code: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="35a81-120">說明</span><span class="sxs-lookup"><span data-stu-id="35a81-120">Explanation</span></span>  
 <span data-ttu-id="35a81-121">這個警告事件表示已讀取預設密碼同步配接器屬性時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="35a81-121">This Warning event indicates that there was an error reading the default password sync adapter properties.</span></span> <span data-ttu-id="35a81-122">每個密碼同步配接器都有與其相關聯的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="35a81-122">Each password sync adapter has configuration properties associated with it.</span></span> <span data-ttu-id="35a81-123">這些屬性會儲存在 SSO 組態存放區，並建立密碼同步配接器時，由 SSO 命令列工具或 SSO 管理 MMC 所建立。</span><span class="sxs-lookup"><span data-stu-id="35a81-123">These properties are stored in the SSO config store and are created by the SSO command line tools or the SSO Admin MMC when the password sync adapter is created.</span></span>  <span data-ttu-id="35a81-124">可以會那里遺失屬性如果 「 密碼同步配接器建立任何其他方法，則可以發出此錯誤。</span><span class="sxs-lookup"><span data-stu-id="35a81-124">There can be missing properties if the password sync adapter was created by any other means, then this error can be issued.</span></span>  

## <a name="user-action"></a><span data-ttu-id="35a81-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="35a81-125">User Action</span></span>  
 <span data-ttu-id="35a81-126">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="35a81-126">To resolve this warning, do one or more of the following:</span></span>  

-   <span data-ttu-id="35a81-127">確認密碼同步配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="35a81-127">Verify password sync adapter properties.</span></span>  

-   <span data-ttu-id="35a81-128">重新建立密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="35a81-128">Recreate the password sync adapter</span></span>  

## <a name="more-info"></a><span data-ttu-id="35a81-129">其他資訊</span><span class="sxs-lookup"><span data-stu-id="35a81-129">More info</span></span>

- <span data-ttu-id="35a81-130">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="35a81-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="35a81-131">密碼同步</span><span class="sxs-lookup"><span data-stu-id="35a81-131">Password Synchronization</span></span>](../core/password-synchronization2.md)
