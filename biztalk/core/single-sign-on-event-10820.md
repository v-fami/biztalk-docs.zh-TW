---
title: 單一登入： 事件 10820 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2da93a2c-d00d-4ca0-a0cf-453cee4bf3c3
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78b566c4dfe4437017b743228c9bae2631c79a00
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011655"
---
# <a name="single-sign-on-event-10820"></a><span data-ttu-id="3b17f-102">單一登入： 事件 10820</span><span class="sxs-lookup"><span data-stu-id="3b17f-102">Single Sign-On: Event 10820</span></span>
## <a name="details"></a><span data-ttu-id="3b17f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3b17f-103">Details</span></span>  
  
|                 |                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------|
|  <span data-ttu-id="3b17f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3b17f-104">Product Name</span></span>   |                                  <span data-ttu-id="3b17f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3b17f-105">Enterprise Single Sign-On</span></span>                                   |
| <span data-ttu-id="3b17f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="3b17f-106">Product Version</span></span> |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                  |
|    <span data-ttu-id="3b17f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3b17f-107">Event ID</span></span>     |                                            <span data-ttu-id="3b17f-108">10820</span><span class="sxs-lookup"><span data-stu-id="3b17f-108">10820</span></span>                                             |
|  <span data-ttu-id="3b17f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="3b17f-109">Event Source</span></span>   |                                            <span data-ttu-id="3b17f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3b17f-110">ENTSSO</span></span>                                            |
|    <span data-ttu-id="3b17f-111">元件</span><span class="sxs-lookup"><span data-stu-id="3b17f-111">Component</span></span>    |                                             <span data-ttu-id="3b17f-112">不適用</span><span class="sxs-lookup"><span data-stu-id="3b17f-112">N/A</span></span>                                              |
|  <span data-ttu-id="3b17f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3b17f-113">Symbolic Name</span></span>  |                                <span data-ttu-id="3b17f-114">ENTSSO_E_REQUIRE_OLD_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="3b17f-114">ENTSSO_E_REQUIRE_OLD_PASSWORD</span></span>                                 |
|  <span data-ttu-id="3b17f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3b17f-115">Message Text</span></span>   | <span data-ttu-id="3b17f-116">變更外部帳戶的密碼時，配接器必須提供舊密碼。</span><span class="sxs-lookup"><span data-stu-id="3b17f-116">When changing the password for an external account the adapter must supply the old password.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="3b17f-117">說明</span><span class="sxs-lookup"><span data-stu-id="3b17f-117">Explanation</span></span>  
 <span data-ttu-id="3b17f-118">此應用程式設定密碼同步配接器，才能提供舊密碼的方式。</span><span class="sxs-lookup"><span data-stu-id="3b17f-118">This application is configured in such a way that the password sync adapter is required to supply the old password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3b17f-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3b17f-119">User Action</span></span>  
 <span data-ttu-id="3b17f-120">請檢查您的密碼同步配接器的組態。</span><span class="sxs-lookup"><span data-stu-id="3b17f-120">Check the configuration of your password sync adapter.</span></span>