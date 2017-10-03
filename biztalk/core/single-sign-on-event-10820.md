---
title: "單一登入： 事件 10820 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2da93a2c-d00d-4ca0-a0cf-453cee4bf3c3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a3ae1be84ca0b936fe38463e51e6385071f7a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10820"></a><span data-ttu-id="5031c-102">單一登入： 事件 10820</span><span class="sxs-lookup"><span data-stu-id="5031c-102">Single Sign-On: Event 10820</span></span>
## <a name="details"></a><span data-ttu-id="5031c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5031c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5031c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5031c-104">Product Name</span></span>|<span data-ttu-id="5031c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5031c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5031c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5031c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5031c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5031c-107">Event ID</span></span>|<span data-ttu-id="5031c-108">10820</span><span class="sxs-lookup"><span data-stu-id="5031c-108">10820</span></span>|  
|<span data-ttu-id="5031c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5031c-109">Event Source</span></span>|<span data-ttu-id="5031c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5031c-110">ENTSSO</span></span>|  
|<span data-ttu-id="5031c-111">元件</span><span class="sxs-lookup"><span data-stu-id="5031c-111">Component</span></span>|<span data-ttu-id="5031c-112">不適用</span><span class="sxs-lookup"><span data-stu-id="5031c-112">N/A</span></span>|  
|<span data-ttu-id="5031c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5031c-113">Symbolic Name</span></span>|<span data-ttu-id="5031c-114">ENTSSO_E_REQUIRE_OLD_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="5031c-114">ENTSSO_E_REQUIRE_OLD_PASSWORD</span></span>|  
|<span data-ttu-id="5031c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5031c-115">Message Text</span></span>|<span data-ttu-id="5031c-116">變更外部帳戶的密碼時，配接器必須提供舊密碼。</span><span class="sxs-lookup"><span data-stu-id="5031c-116">When changing the password for an external account the adapter must supply the old password.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5031c-117">說明</span><span class="sxs-lookup"><span data-stu-id="5031c-117">Explanation</span></span>  
 <span data-ttu-id="5031c-118">此應用程式設定的方式，密碼同步配接器，就需要提供舊密碼。</span><span class="sxs-lookup"><span data-stu-id="5031c-118">This application is configured in such a way that the password sync adapter is required to supply the old password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5031c-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5031c-119">User Action</span></span>  
 <span data-ttu-id="5031c-120">請檢查您的密碼同步配接器組態。</span><span class="sxs-lookup"><span data-stu-id="5031c-120">Check the configuration of your password sync adapter.</span></span>