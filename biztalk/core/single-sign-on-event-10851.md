---
title: 單一登入： 事件 10851 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 582b92bf-2833-47cd-b685-1245e870d81d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15121c1d7829f04bd9c106ed71da391d401ae564
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987231"
---
# <a name="single-sign-on-event-10851"></a><span data-ttu-id="c98b3-102">單一登入： 事件 10851</span><span class="sxs-lookup"><span data-stu-id="c98b3-102">Single Sign-On: Event 10851</span></span>
## <a name="details"></a><span data-ttu-id="c98b3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c98b3-103">Details</span></span>  
  
|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="c98b3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c98b3-104">Product Name</span></span>   |                                             <span data-ttu-id="c98b3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c98b3-105">Enterprise Single Sign-On</span></span>                                             |
| <span data-ttu-id="c98b3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c98b3-106">Product Version</span></span> |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    <span data-ttu-id="c98b3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c98b3-107">Event ID</span></span>     |                                                       <span data-ttu-id="c98b3-108">10851</span><span class="sxs-lookup"><span data-stu-id="c98b3-108">10851</span></span>                                                       |
|  <span data-ttu-id="c98b3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c98b3-109">Event Source</span></span>   |                                                      <span data-ttu-id="c98b3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c98b3-110">ENTSSO</span></span>                                                       |
|    <span data-ttu-id="c98b3-111">元件</span><span class="sxs-lookup"><span data-stu-id="c98b3-111">Component</span></span>    |                                                        <span data-ttu-id="c98b3-112">不適用</span><span class="sxs-lookup"><span data-stu-id="c98b3-112">N/A</span></span>                                                        |
|  <span data-ttu-id="c98b3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c98b3-113">Symbolic Name</span></span>  |                                     <span data-ttu-id="c98b3-114">ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC</span><span class="sxs-lookup"><span data-stu-id="c98b3-114">ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC</span></span>                                      |
|  <span data-ttu-id="c98b3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c98b3-115">Message Text</span></span>   | <span data-ttu-id="c98b3-116">應用程式無法指派給密碼同步配接器，因為它已設定「直接密碼同步」旗標。</span><span class="sxs-lookup"><span data-stu-id="c98b3-116">The application cannot be assigned to a password sync adapter because it has the 'direct password sync' flag set.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="c98b3-117">說明</span><span class="sxs-lookup"><span data-stu-id="c98b3-117">Explanation</span></span>  
 <span data-ttu-id="c98b3-118">應用程式無法同時使用直接密碼同步和密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="c98b3-118">An application cannot use both direct password sync and a password sync adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c98b3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c98b3-119">User Action</span></span>  
 <span data-ttu-id="c98b3-120">檢閱您的應用程式，並決定是否應該使用直接密碼同步。如果應該使用，保留旗標設定狀態，並且不要嘗試將應用程式指派至密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="c98b3-120">Review your application and decide whether or not it should have direct password sync. If it should, leave the flag set as it is and do not attempt to assign the application to a password sync adapter.</span></span> <span data-ttu-id="c98b3-121">如果不應，然後關閉此旗標，並指派適當的密碼同步配接器應用程式。</span><span class="sxs-lookup"><span data-stu-id="c98b3-121">If it should not, then turn the flag off and assign the application to a password sync adapter as appropriate.</span></span>