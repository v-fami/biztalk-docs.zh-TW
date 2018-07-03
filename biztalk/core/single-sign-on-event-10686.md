---
title: 單一登入： 事件 10686 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3e71f2a-e51d-4736-b06a-117142d30dae
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 363ec7268ca3088a4d7658bbf4497099c810f92f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987985"
---
# <a name="single-sign-on-event-10686"></a><span data-ttu-id="baa56-102">單一登入： 事件 10686</span><span class="sxs-lookup"><span data-stu-id="baa56-102">Single Sign-On: Event 10686</span></span>
## <a name="details"></a><span data-ttu-id="baa56-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="baa56-103">Details</span></span>  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  <span data-ttu-id="baa56-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="baa56-104">Product Name</span></span>   |                         <span data-ttu-id="baa56-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="baa56-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="baa56-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="baa56-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    <span data-ttu-id="baa56-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="baa56-107">Event ID</span></span>     |                                   <span data-ttu-id="baa56-108">10686</span><span class="sxs-lookup"><span data-stu-id="baa56-108">10686</span></span>                                   |
|  <span data-ttu-id="baa56-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="baa56-109">Event Source</span></span>   |                                  <span data-ttu-id="baa56-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="baa56-110">ENTSSO</span></span>                                   |
|    <span data-ttu-id="baa56-111">元件</span><span class="sxs-lookup"><span data-stu-id="baa56-111">Component</span></span>    |                                    <span data-ttu-id="baa56-112">N\A</span><span class="sxs-lookup"><span data-stu-id="baa56-112">N\A</span></span>                                    |
|  <span data-ttu-id="baa56-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="baa56-113">Symbolic Name</span></span>  |                          <span data-ttu-id="baa56-114">SSO_INFO_REPLAY_STARTED</span><span class="sxs-lookup"><span data-stu-id="baa56-114">SSO_INFO_REPLAY_STARTED</span></span>                          |
|  <span data-ttu-id="baa56-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="baa56-115">Message Text</span></span>   | <span data-ttu-id="baa56-116">重新執行預存外部密碼 changes.%r</span><span class="sxs-lookup"><span data-stu-id="baa56-116">Replaying stored external password changes.%r</span></span><br /><br /> <span data-ttu-id="baa56-117">重新執行檔案： %1</span><span class="sxs-lookup"><span data-stu-id="baa56-117">Replay File: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="baa56-118">說明</span><span class="sxs-lookup"><span data-stu-id="baa56-118">Explanation</span></span>  
 <span data-ttu-id="baa56-119">這個資訊事件表示 SSO 已重新執行預存外部密碼變更檔案。</span><span class="sxs-lookup"><span data-stu-id="baa56-119">This Information event indicates that SSO is replaying the stored external password changes file.</span></span> <span data-ttu-id="baa56-120">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="baa56-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span>  

## <a name="user-action"></a><span data-ttu-id="baa56-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="baa56-121">User Action</span></span>  

- <span data-ttu-id="baa56-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="baa56-122">No user action is necessary.</span></span>  

  <span data-ttu-id="baa56-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="baa56-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="baa56-124">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="baa56-124">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="baa56-125">密碼同步</span><span class="sxs-lookup"><span data-stu-id="baa56-125">Password Synchronization</span></span>](../core/password-synchronization2.md)
