---
title: 單一登入： 事件 10533 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31abd828-5f10-43f7-b99e-f3195250130c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2fd77728e459c544a9934e5d27f28a9ea092c67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008879"
---
# <a name="single-sign-on-event-10533"></a><span data-ttu-id="03b01-102">單一登入： 事件 10533</span><span class="sxs-lookup"><span data-stu-id="03b01-102">Single Sign-On: Event 10533</span></span>
## <a name="details"></a><span data-ttu-id="03b01-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="03b01-103">Details</span></span>  

|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="03b01-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="03b01-104">Product Name</span></span>   |                                             <span data-ttu-id="03b01-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="03b01-105">Enterprise Single Sign-On</span></span>                                             |
| <span data-ttu-id="03b01-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="03b01-106">Product Version</span></span> |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    <span data-ttu-id="03b01-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="03b01-107">Event ID</span></span>     |                                                       <span data-ttu-id="03b01-108">10533</span><span class="sxs-lookup"><span data-stu-id="03b01-108">10533</span></span>                                                       |
|  <span data-ttu-id="03b01-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="03b01-109">Event Source</span></span>   |                                                      <span data-ttu-id="03b01-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="03b01-110">ENTSSO</span></span>                                                       |
|    <span data-ttu-id="03b01-111">元件</span><span class="sxs-lookup"><span data-stu-id="03b01-111">Component</span></span>    |                                                        <span data-ttu-id="03b01-112">N\A</span><span class="sxs-lookup"><span data-stu-id="03b01-112">N\A</span></span>                                                        |
|  <span data-ttu-id="03b01-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="03b01-113">Symbolic Name</span></span>  |                                            <span data-ttu-id="03b01-114">SSO_INFO_GOT_CURRENT_SECRET</span><span class="sxs-lookup"><span data-stu-id="03b01-114">SSO_INFO_GOT_CURRENT_SECRET</span></span>                                            |
|  <span data-ttu-id="03b01-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="03b01-115">Message Text</span></span>   | <span data-ttu-id="03b01-116">從主要祕密 server.%r 取得目前的祕密</span><span class="sxs-lookup"><span data-stu-id="03b01-116">Got the current secret from the master secret server.%r</span></span><br /><br /> <span data-ttu-id="03b01-117">祕密伺服器名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="03b01-117">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="03b01-118">MSID: %2</span><span class="sxs-lookup"><span data-stu-id="03b01-118">MSID: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="03b01-119">說明</span><span class="sxs-lookup"><span data-stu-id="03b01-119">Explanation</span></span>  
 <span data-ttu-id="03b01-120">這個資訊事件表示 SSO 具有目前的主要祕密。</span><span class="sxs-lookup"><span data-stu-id="03b01-120">This Information event indicates that SSO has the current master secret.</span></span>  

## <a name="user-action"></a><span data-ttu-id="03b01-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="03b01-121">User Action</span></span>  

- <span data-ttu-id="03b01-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="03b01-122">No user action is necessary.</span></span>  

  <span data-ttu-id="03b01-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="03b01-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="03b01-124">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="03b01-124">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  

- [<span data-ttu-id="03b01-125">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="03b01-125">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
