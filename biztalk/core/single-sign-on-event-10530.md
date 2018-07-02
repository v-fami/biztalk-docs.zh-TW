---
title: 單一登入： 事件 10530 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bb37305-26fe-46a7-958d-3ed7f6876a7b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38eb770f795d23286b2a057a428e3bfec73e1674
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974879"
---
# <a name="single-sign-on-event-10530"></a><span data-ttu-id="d01bd-102">單一登入： 事件 10530</span><span class="sxs-lookup"><span data-stu-id="d01bd-102">Single Sign-On: Event 10530</span></span>
## <a name="details"></a><span data-ttu-id="d01bd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d01bd-103">Details</span></span>  

|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d01bd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d01bd-104">Product Name</span></span>   |                                             <span data-ttu-id="d01bd-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d01bd-105">Enterprise Single Sign-On</span></span>                                              |
| <span data-ttu-id="d01bd-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d01bd-106">Product Version</span></span> |                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    <span data-ttu-id="d01bd-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d01bd-107">Event ID</span></span>     |                                                       <span data-ttu-id="d01bd-108">10530</span><span class="sxs-lookup"><span data-stu-id="d01bd-108">10530</span></span>                                                        |
|  <span data-ttu-id="d01bd-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d01bd-109">Event Source</span></span>   |                                                       <span data-ttu-id="d01bd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d01bd-110">ENTSSO</span></span>                                                       |
|    <span data-ttu-id="d01bd-111">元件</span><span class="sxs-lookup"><span data-stu-id="d01bd-111">Component</span></span>    |                                                        <span data-ttu-id="d01bd-112">N\A</span><span class="sxs-lookup"><span data-stu-id="d01bd-112">N\A</span></span>                                                         |
|  <span data-ttu-id="d01bd-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d01bd-113">Symbolic Name</span></span>  |                                            <span data-ttu-id="d01bd-114">SSO_INFO_GOT_PREVIOUS_SECRET</span><span class="sxs-lookup"><span data-stu-id="d01bd-114">SSO_INFO_GOT_PREVIOUS_SECRET</span></span>                                            |
|  <span data-ttu-id="d01bd-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d01bd-115">Message Text</span></span>   | <span data-ttu-id="d01bd-116">從主要密碼伺服器取得先前的密碼。%r</span><span class="sxs-lookup"><span data-stu-id="d01bd-116">Got the previous secret from the master secret server.%r</span></span><br /><br /> <span data-ttu-id="d01bd-117">祕密伺服器名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="d01bd-117">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="d01bd-118">MSID: %2</span><span class="sxs-lookup"><span data-stu-id="d01bd-118">MSID: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="d01bd-119">說明</span><span class="sxs-lookup"><span data-stu-id="d01bd-119">Explanation</span></span>  
 <span data-ttu-id="d01bd-120">這個資訊事件表示 SSO 具有先前的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="d01bd-120">This Information event indicates that SSO has the previous master secret.</span></span>  

## <a name="user-action"></a><span data-ttu-id="d01bd-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d01bd-121">User Action</span></span>  

- <span data-ttu-id="d01bd-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="d01bd-122">No user action is necessary.</span></span>  

  <span data-ttu-id="d01bd-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="d01bd-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="d01bd-124">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="d01bd-124">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  

- [<span data-ttu-id="d01bd-125">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="d01bd-125">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
