---
title: 單一登入： 事件 10749 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10986736-77c0-42a7-b2bb-cd20f9f75fa6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf82eb2fc8312874947af3c035dc13bb8e39a46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010973"
---
# <a name="single-sign-on-event-10749"></a><span data-ttu-id="2ef6e-102">單一登入： 事件 10749</span><span class="sxs-lookup"><span data-stu-id="2ef6e-102">Single Sign-On: Event 10749</span></span>
## <a name="details"></a><span data-ttu-id="2ef6e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2ef6e-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="2ef6e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2ef6e-104">Product Name</span></span>   |                                                                                                                      <span data-ttu-id="2ef6e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2ef6e-105">Enterprise Single Sign-On</span></span>                                                                                                                      |
| <span data-ttu-id="2ef6e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2ef6e-106">Product Version</span></span> |                                                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                      |
|    <span data-ttu-id="2ef6e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2ef6e-107">Event ID</span></span>     |                                                                                                                                <span data-ttu-id="2ef6e-108">10749</span><span class="sxs-lookup"><span data-stu-id="2ef6e-108">10749</span></span>                                                                                                                                |
|  <span data-ttu-id="2ef6e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2ef6e-109">Event Source</span></span>   |                                                                                                                               <span data-ttu-id="2ef6e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2ef6e-110">ENTSSO</span></span>                                                                                                                                |
|    <span data-ttu-id="2ef6e-111">元件</span><span class="sxs-lookup"><span data-stu-id="2ef6e-111">Component</span></span>    |                                                                                                                                 <span data-ttu-id="2ef6e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="2ef6e-112">N\A</span></span>                                                                                                                                 |
|  <span data-ttu-id="2ef6e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2ef6e-113">Symbolic Name</span></span>  |                                                                                                                       <span data-ttu-id="2ef6e-114">SSO_WARN_PS_CLIENT_PING</span><span class="sxs-lookup"><span data-stu-id="2ef6e-114">SSO_WARN_PS_CLIENT_PING</span></span>                                                                                                                       |
|  <span data-ttu-id="2ef6e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2ef6e-115">Message Text</span></span>   | <span data-ttu-id="2ef6e-116">無法連絡目的地 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2ef6e-116">Could not contact the destination SSO server.</span></span><br /><br /> <span data-ttu-id="2ef6e-117">請檢查 SSO 服務正在該伺服器上，以及它可以是 contacted.%r</span><span class="sxs-lookup"><span data-stu-id="2ef6e-117">Check that the SSO service is running on that server and that it can be contacted.%r</span></span><br /><br /> <span data-ttu-id="2ef6e-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2ef6e-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="2ef6e-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="2ef6e-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="2ef6e-120">SSO 伺服器名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="2ef6e-120">SSO Server Name: %3%r</span></span><br /><br /> <span data-ttu-id="2ef6e-121">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="2ef6e-121">Error Code: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="2ef6e-122">說明</span><span class="sxs-lookup"><span data-stu-id="2ef6e-122">Explanation</span></span>  
 <span data-ttu-id="2ef6e-123">這個警告事件表示 SSO 密碼同步處理無法連絡指定的目的地 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2ef6e-123">This Warning event indicates that SSO Password Sync could not contact the specified destination SSO server.</span></span>  

## <a name="user-action"></a><span data-ttu-id="2ef6e-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2ef6e-124">User Action</span></span>  
 <span data-ttu-id="2ef6e-125">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="2ef6e-125">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="2ef6e-126">使用 ENTSSO 伺服器嵌入式管理單元來檢查伺服器。</span><span class="sxs-lookup"><span data-stu-id="2ef6e-126">Use the ENTSSO Servers Snap-In to check the server.</span></span>  

- <span data-ttu-id="2ef6e-127">如果未執行，請啟動 「 企業單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="2ef6e-127">Start the Enterprise Single Sign-On Service if it is not running.</span></span>  

- <span data-ttu-id="2ef6e-128">請檢查目的地 SSO 伺服器的網路連線。</span><span class="sxs-lookup"><span data-stu-id="2ef6e-128">Check the network connection to the destination SSO server.</span></span>  

- <span data-ttu-id="2ef6e-129">請檢查目的地 SSO 伺服器上的防火牆。</span><span class="sxs-lookup"><span data-stu-id="2ef6e-129">Check firewall on the destination SSO Server.</span></span>  

  <span data-ttu-id="2ef6e-130">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="2ef6e-130">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="2ef6e-131">如何使用伺服器嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="2ef6e-131">How to Use the Servers Snap-in</span></span>](../core/how-to-use-the-servers-snap-in.md)
