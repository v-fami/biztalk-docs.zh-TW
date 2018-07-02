---
title: 單一登入： 事件 10819 |Microsoft Docs
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
ms.openlocfilehash: f196bb49cd0e5825551bbffe45757c327e2cbcca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972111"
---
# <a name="single-sign-on-event-10819"></a><span data-ttu-id="0cbf3-102">單一登入： 事件 10819</span><span class="sxs-lookup"><span data-stu-id="0cbf3-102">Single Sign-On: Event 10819</span></span>
## <a name="details"></a><span data-ttu-id="0cbf3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cbf3-103">Details</span></span>  
  
|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  <span data-ttu-id="0cbf3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0cbf3-104">Product Name</span></span>   |                         <span data-ttu-id="0cbf3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0cbf3-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="0cbf3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0cbf3-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    <span data-ttu-id="0cbf3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0cbf3-107">Event ID</span></span>     |                                   <span data-ttu-id="0cbf3-108">10819</span><span class="sxs-lookup"><span data-stu-id="0cbf3-108">10819</span></span>                                   |
|  <span data-ttu-id="0cbf3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0cbf3-109">Event Source</span></span>   |                                  <span data-ttu-id="0cbf3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0cbf3-110">ENTSSO</span></span>                                   |
|    <span data-ttu-id="0cbf3-111">元件</span><span class="sxs-lookup"><span data-stu-id="0cbf3-111">Component</span></span>    |                                    <span data-ttu-id="0cbf3-112">不適用</span><span class="sxs-lookup"><span data-stu-id="0cbf3-112">N/A</span></span>                                    |
|  <span data-ttu-id="0cbf3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0cbf3-113">Symbolic Name</span></span>  |                         <span data-ttu-id="0cbf3-114">ENTSSO_E_MAPPING_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="0cbf3-114">ENTSSO_E_MAPPING_CONFLICT</span></span>                         |
|  <span data-ttu-id="0cbf3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0cbf3-115">Message Text</span></span>   | <span data-ttu-id="0cbf3-116">外部帳戶未更新，因為有對應衝突。</span><span class="sxs-lookup"><span data-stu-id="0cbf3-116">The external account was not updated because there is a mapping conflict.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0cbf3-117">說明</span><span class="sxs-lookup"><span data-stu-id="0cbf3-117">Explanation</span></span>  
 <span data-ttu-id="0cbf3-118">外部帳戶未更新，因為有對應衝突。</span><span class="sxs-lookup"><span data-stu-id="0cbf3-118">The external account was not updated because there is a mapping conflict.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0cbf3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0cbf3-119">User Action</span></span>  
 <span data-ttu-id="0cbf3-120">如果這是預期中的行為，則不需要任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="0cbf3-120">If this is expected behavior then no action is required, this message is informational only.</span></span> <span data-ttu-id="0cbf3-121">如果應該允許對應衝突，則據此設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cbf3-121">If mapping conflicts should be allowed then configure the application accordingly.</span></span>  
  
 <span data-ttu-id="0cbf3-122">如需有關對應衝突的詳細資訊，請參閱**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="0cbf3-122">For more information on mapping conflicts, see **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>