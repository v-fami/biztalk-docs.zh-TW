---
title: 單一登入： 事件 10819 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffa5e977-c8b9-4568-8963-0d4cf44b5637
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f2a98586d9c139674c64db6ca03aaa6abd6ba6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276430"
---
# <a name="single-sign-on-event-10819"></a><span data-ttu-id="2a749-102">單一登入： 事件 10819</span><span class="sxs-lookup"><span data-stu-id="2a749-102">Single Sign-On: Event 10819</span></span>
## <a name="details"></a><span data-ttu-id="2a749-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2a749-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a749-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2a749-104">Product Name</span></span>|<span data-ttu-id="2a749-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2a749-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2a749-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2a749-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2a749-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2a749-107">Event ID</span></span>|<span data-ttu-id="2a749-108">10819</span><span class="sxs-lookup"><span data-stu-id="2a749-108">10819</span></span>|  
|<span data-ttu-id="2a749-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2a749-109">Event Source</span></span>|<span data-ttu-id="2a749-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2a749-110">ENTSSO</span></span>|  
|<span data-ttu-id="2a749-111">元件</span><span class="sxs-lookup"><span data-stu-id="2a749-111">Component</span></span>|<span data-ttu-id="2a749-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2a749-112">N/A</span></span>|  
|<span data-ttu-id="2a749-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2a749-113">Symbolic Name</span></span>|<span data-ttu-id="2a749-114">ENTSSO_E_MAPPING_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="2a749-114">ENTSSO_E_MAPPING_CONFLICT</span></span>|  
|<span data-ttu-id="2a749-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2a749-115">Message Text</span></span>|<span data-ttu-id="2a749-116">外部帳戶未更新，因為有對應衝突。</span><span class="sxs-lookup"><span data-stu-id="2a749-116">The external account was not updated because there is a mapping conflict.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2a749-117">說明</span><span class="sxs-lookup"><span data-stu-id="2a749-117">Explanation</span></span>  
 <span data-ttu-id="2a749-118">外部帳戶未更新，因為有對應衝突。</span><span class="sxs-lookup"><span data-stu-id="2a749-118">The external account was not updated because there is a mapping conflict.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2a749-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2a749-119">User Action</span></span>  
 <span data-ttu-id="2a749-120">如果這是預期中的行為，則不需要任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="2a749-120">If this is expected behavior then no action is required, this message is informational only.</span></span> <span data-ttu-id="2a749-121">如果應該允許對應衝突，則據此設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a749-121">If mapping conflicts should be allowed then configure the application accordingly.</span></span>  
  
 <span data-ttu-id="2a749-122">如需對應衝突的詳細資訊，請參閱**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a749-122">For more information on mapping conflicts, see **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>