---
title: 單一登入： 事件 10532 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae2112bc-b53c-4d99-9dc1-a2f55dda4665
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 135060013686ff24e4f2692bda0e8829189e1c4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974847"
---
# <a name="single-sign-on-event-10532"></a><span data-ttu-id="15db4-102">單一登入： 事件 10532</span><span class="sxs-lookup"><span data-stu-id="15db4-102">Single Sign-On: Event 10532</span></span>
## <a name="details"></a><span data-ttu-id="15db4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="15db4-103">Details</span></span>  

|                 |                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="15db4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="15db4-104">Product Name</span></span>   |                                                                              <span data-ttu-id="15db4-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="15db4-105">Enterprise Single Sign-On</span></span>                                                                              |
| <span data-ttu-id="15db4-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="15db4-106">Product Version</span></span> |                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                              |
|    <span data-ttu-id="15db4-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="15db4-107">Event ID</span></span>     |                                                                                        <span data-ttu-id="15db4-108">10532</span><span class="sxs-lookup"><span data-stu-id="15db4-108">10532</span></span>                                                                                        |
|  <span data-ttu-id="15db4-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="15db4-109">Event Source</span></span>   |                                                                                       <span data-ttu-id="15db4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="15db4-110">ENTSSO</span></span>                                                                                        |
|    <span data-ttu-id="15db4-111">元件</span><span class="sxs-lookup"><span data-stu-id="15db4-111">Component</span></span>    |                                                                                         <span data-ttu-id="15db4-112">CO</span><span class="sxs-lookup"><span data-stu-id="15db4-112">CO</span></span>                                                                                          |
|  <span data-ttu-id="15db4-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="15db4-113">Symbolic Name</span></span>  |                                                                             <span data-ttu-id="15db4-114">SSO_WARN_LOST_SECRET_SERVER</span><span class="sxs-lookup"><span data-stu-id="15db4-114">SSO_WARN_LOST_SECRET_SERVER</span></span>                                                                             |
|  <span data-ttu-id="15db4-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="15db4-115">Message Text</span></span>   | <span data-ttu-id="15db4-116">無法擷取主要密碼。</span><span class="sxs-lookup"><span data-stu-id="15db4-116">Failed to retrieve master secrets.</span></span> <span data-ttu-id="15db4-117">確認主要密碼伺服器名稱是否正確以及是否可用。%r</span><span class="sxs-lookup"><span data-stu-id="15db4-117">Verify that the master secret server name is correct and that it is available.%r</span></span><br /><br /> <span data-ttu-id="15db4-118">祕密伺服器名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="15db4-118">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="15db4-119">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="15db4-119">Error Code: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="15db4-120">說明</span><span class="sxs-lookup"><span data-stu-id="15db4-120">Explanation</span></span>  
 <span data-ttu-id="15db4-121">這個警告事件表示取得主要密碼的要求已經失敗。</span><span class="sxs-lookup"><span data-stu-id="15db4-121">This Warning event indicates that a request to get the master secret has failed.</span></span> <span data-ttu-id="15db4-122">這可能是因為「企業單一登入」服務未在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="15db4-122">This might be because the Enterprise Single Sign-On service is not running on the server.</span></span>  

## <a name="user-action"></a><span data-ttu-id="15db4-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="15db4-123">User Action</span></span>  
 <span data-ttu-id="15db4-124">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="15db4-124">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="15db4-125">檢查應用程式事件記錄檔相關聯的事件或錯誤。</span><span class="sxs-lookup"><span data-stu-id="15db4-125">Check the Application event log for associated events or errors.</span></span>  

- <span data-ttu-id="15db4-126">請確認主要密碼伺服器名稱是正確的。</span><span class="sxs-lookup"><span data-stu-id="15db4-126">Verify the master secret server name is correct.</span></span>  

- <span data-ttu-id="15db4-127">請確認主要密碼伺服器連線且「企業單一登入」服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="15db4-127">Verify the master secret server is online and that the Enterprise Single Sign-On service is running.</span></span>  

  <span data-ttu-id="15db4-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="15db4-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="15db4-129">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="15db4-129">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  

- [<span data-ttu-id="15db4-130">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="15db4-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
