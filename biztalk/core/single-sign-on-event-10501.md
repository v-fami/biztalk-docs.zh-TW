---
title: 單一登入： 事件 10501 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d615c01-4e80-4c40-ae15-fd1c48853474
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e45e8b471fb7e00dad84e30633dac11ea54e2ac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011751"
---
# <a name="single-sign-on-event-10501"></a><span data-ttu-id="1c5e7-102">單一登入： 事件 10501</span><span class="sxs-lookup"><span data-stu-id="1c5e7-102">Single Sign-On: Event 10501</span></span>
## <a name="details"></a><span data-ttu-id="1c5e7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1c5e7-103">Details</span></span>  

|                 |                                                                                                                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1c5e7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1c5e7-104">Product Name</span></span>   |                                                                                              <span data-ttu-id="1c5e7-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1c5e7-105">Enterprise Single Sign-On</span></span>                                                                                               |
| <span data-ttu-id="1c5e7-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="1c5e7-106">Product Version</span></span> |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                              |
|    <span data-ttu-id="1c5e7-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1c5e7-107">Event ID</span></span>     |                                                                                                        <span data-ttu-id="1c5e7-108">10501</span><span class="sxs-lookup"><span data-stu-id="1c5e7-108">10501</span></span>                                                                                                         |
|  <span data-ttu-id="1c5e7-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1c5e7-109">Event Source</span></span>   |                                                                                                        <span data-ttu-id="1c5e7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1c5e7-110">ENTSSO</span></span>                                                                                                        |
|    <span data-ttu-id="1c5e7-111">元件</span><span class="sxs-lookup"><span data-stu-id="1c5e7-111">Component</span></span>    |                                                                                                         <span data-ttu-id="1c5e7-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1c5e7-112">N\A</span></span>                                                                                                          |
|  <span data-ttu-id="1c5e7-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1c5e7-113">Symbolic Name</span></span>  |                                                                                              <span data-ttu-id="1c5e7-114">SSO_INFO_SERVICE_STARTING</span><span class="sxs-lookup"><span data-stu-id="1c5e7-114">SSO_INFO_SERVICE_STARTING</span></span>                                                                                               |
|  <span data-ttu-id="1c5e7-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1c5e7-115">Message Text</span></span>   | <span data-ttu-id="1c5e7-116">SSO 服務正在 starting.%r</span><span class="sxs-lookup"><span data-stu-id="1c5e7-116">The SSO service is starting.%r</span></span><br /><br /> <span data-ttu-id="1c5e7-117">電腦名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="1c5e7-117">Computer Name: %1%r</span></span><br /><br /> <span data-ttu-id="1c5e7-118">SQL Server 名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="1c5e7-118">SQL Server Name: %2%r</span></span><br /><br /> <span data-ttu-id="1c5e7-119">SSO 資料庫名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="1c5e7-119">SSO Database Name: %3%r</span></span><br /><br /> <span data-ttu-id="1c5e7-120">使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="1c5e7-120">Using SSL.</span></span> <span data-ttu-id="1c5e7-121">SQL Server 連線強制執行通訊協定加密。</span><span class="sxs-lookup"><span data-stu-id="1c5e7-121">Protocol encryption enforced for SQL Server connections.</span></span> |

## <a name="explanation"></a><span data-ttu-id="1c5e7-122">說明</span><span class="sxs-lookup"><span data-stu-id="1c5e7-122">Explanation</span></span>  
 <span data-ttu-id="1c5e7-123">這個資訊事件表示 SSO 服務正在啟動與指定的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="1c5e7-123">This Information event indicates that the SSO service is starting with the configuration properties indicated.</span></span>  

## <a name="user-action"></a><span data-ttu-id="1c5e7-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1c5e7-124">User Action</span></span>  
 <span data-ttu-id="1c5e7-125">若要解決這個錯誤事件，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1c5e7-125">To resolve this error event, do the following:</span></span>  

- <span data-ttu-id="1c5e7-126">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="1c5e7-126">No action is necessary.</span></span>  

  <span data-ttu-id="1c5e7-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="1c5e7-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="1c5e7-128">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="1c5e7-128">Using SSO</span></span>](../core/using-sso.md)
