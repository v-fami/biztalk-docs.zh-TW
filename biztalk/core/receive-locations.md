---
title: 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, properties
- receive locations, about receive locations
- receive locations
- receive locations, receive location types
ms.assetid: be5f7e5d-b63f-42f6-985e-895ba3912d34
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15ee246c07fa471cefe8f4dc42f55b0543bb8419
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024260"
---
# <a name="receive-locations"></a><span data-ttu-id="98adf-102">接收位置</span><span class="sxs-lookup"><span data-stu-id="98adf-102">Receive Locations</span></span>
<span data-ttu-id="98adf-103">建立接收位置牽涉到指定輸入訊息會送達的位址，而處理訊息的傳訊管線也會在該位址處理訊息。</span><span class="sxs-lookup"><span data-stu-id="98adf-103">Creating a receive location involves specifying an address at which inbound messages arrive and the messaging pipeline that processes the message received at that address.</span></span> <span data-ttu-id="98adf-104">只有系統管理員可以建立和啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="98adf-104">Only administrators can create and enable receive locations.</span></span>  
  
 <span data-ttu-id="98adf-105">系統管理員可以使用 BizTalk 管理主控台來建立接收位置、將接收位置繫結至協調流程、啟用接收位置、停用接收位置，以及設定接收位置的全域屬性。</span><span class="sxs-lookup"><span data-stu-id="98adf-105">An administrator uses the BizTalk Administration Console to create receive locations, bind receive locations to orchestrations, enable receive locations, disable receive locations, and set global properties for receive locations.</span></span>  
  
 <span data-ttu-id="98adf-106">使用 BizTalk 管理主控台的系統管理員會依照下列步驟來建立接收位置：</span><span class="sxs-lookup"><span data-stu-id="98adf-106">An administrator (using the BizTalk Administration Console) follows these steps to create a receive location:</span></span>  
  
1.  <span data-ttu-id="98adf-107">建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="98adf-107">Creates a receive location.</span></span>  
  
2.  <span data-ttu-id="98adf-108">將接收位置與主控件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="98adf-108">Associates the receive location with a host.</span></span>  
  
3.  <span data-ttu-id="98adf-109">將接收位置繫結到協調流程。</span><span class="sxs-lookup"><span data-stu-id="98adf-109">Binds the receive location to an orchestration.</span></span>  
  
4.  <span data-ttu-id="98adf-110">啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="98adf-110">Enables the receive location.</span></span>  
  
5.  <span data-ttu-id="98adf-111">接收位置接收訊息。</span><span class="sxs-lookup"><span data-stu-id="98adf-111">The receive location receives messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98adf-112">使用 Windows Management Instrumentation (WMI) 對接收位置所做的變更，會影響 BizTalk 管理主控台中顯示接收位置的情形。</span><span class="sxs-lookup"><span data-stu-id="98adf-112">Changes to receive locations made by using Windows Management Instrumentation (WMI) affect how receive locations appear in the BizTalk Administration Console.</span></span> <span data-ttu-id="98adf-113">例如，如果系統管理員使用 WMI 建立新的接收位置，該接收位置就會出現在 BizTalk 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="98adf-113">For example, if an administrator uses WMI to create a new receive location, that receive location appears in the BizTalk Administration Console.</span></span> <span data-ttu-id="98adf-114">同樣地，若系統管理員刪除接收位置，該接收位置就會在 BizTalk 管理主控台中消失。</span><span class="sxs-lookup"><span data-stu-id="98adf-114">Similarly, if an administrator deletes a receive location, the receive location disappears from the BizTalk Administration Console.</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="98adf-115">每個接收位置都必須有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="98adf-115">Each receive location must have a unique name.</span></span> <span data-ttu-id="98adf-116">兩個接收位置不能有相同的名稱，在同一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。</span><span class="sxs-lookup"><span data-stu-id="98adf-116">Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]deployment.</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="98adf-117">建議您在接收位置的放置位置中設定強式存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="98adf-117">We recommend that you set strong access control lists (ACL) in the drop location for the receive locations.</span></span> <span data-ttu-id="98adf-118">例如，您必須在檔案接收位置拾取訊息的目錄中設定強式 ACL，讓只有經過授權的使用者可以在此位置放置訊息。</span><span class="sxs-lookup"><span data-stu-id="98adf-118">For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.</span></span>  
  
## <a name="receive-location-types"></a><span data-ttu-id="98adf-119">接收位置類型</span><span class="sxs-lookup"><span data-stu-id="98adf-119">Receive Location Types</span></span>  
 <span data-ttu-id="98adf-120">接收位置有兩種類型</span><span class="sxs-lookup"><span data-stu-id="98adf-120">There are two types of receive locations</span></span>  
  
-   <span data-ttu-id="98adf-121">單向。</span><span class="sxs-lookup"><span data-stu-id="98adf-121">One-way.</span></span> <span data-ttu-id="98adf-122">用在應用程式放置訊息但不等候同步回覆時。</span><span class="sxs-lookup"><span data-stu-id="98adf-122">Used for applications that drop off a message and do not wait for a synchronous reply.</span></span>  
  
-   <span data-ttu-id="98adf-123">要求-回應。</span><span class="sxs-lookup"><span data-stu-id="98adf-123">Request-response.</span></span> <span data-ttu-id="98adf-124">用在應用程式需要訊息的回應時。</span><span class="sxs-lookup"><span data-stu-id="98adf-124">Used with applications that require a response to a message.</span></span>  
  
## <a name="receive-location-properties"></a><span data-ttu-id="98adf-125">接收位置屬性</span><span class="sxs-lookup"><span data-stu-id="98adf-125">Receive Location Properties</span></span>  
 <span data-ttu-id="98adf-126">接收位置具有全域屬性與配接器特有的屬性。</span><span class="sxs-lookup"><span data-stu-id="98adf-126">Receive locations have global and adapter-specific properties.</span></span> <span data-ttu-id="98adf-127">使用 BizTalk 管理主控台的系統管理員，可設定所有與特定配接器相關的接收位置的全域屬性。</span><span class="sxs-lookup"><span data-stu-id="98adf-127">Administrators, using the BizTalk Administration Console, set global properties for all of the receive locations associated with a specific adapter.</span></span>  
  
 <span data-ttu-id="98adf-128">接收位置屬性的變更會相繼發生。</span><span class="sxs-lookup"><span data-stu-id="98adf-128">Changes to receive location properties happen sequentially.</span></span> <span data-ttu-id="98adf-129">若解決方案開發人員修改了特定接收位置的屬性值，則新的屬性值會覆寫系統管理員在 BizTalk 管理主控台中為該接收位置設定的全域屬性值。</span><span class="sxs-lookup"><span data-stu-id="98adf-129">If a solutions developer modifies a property value for a specific receive location, the new property value overrides the global property value for that receive location that the administrator set in the BizTalk Administration Console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98adf-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98adf-130">See Also</span></span>  
 <span data-ttu-id="98adf-131">[管理接收位置](../core/managing-receive-locations.md) </span><span class="sxs-lookup"><span data-stu-id="98adf-131">[Managing Receive Locations](../core/managing-receive-locations.md) </span></span>  
 [<span data-ttu-id="98adf-132">成品</span><span class="sxs-lookup"><span data-stu-id="98adf-132">Artifacts</span></span>](../core/artifacts.md)