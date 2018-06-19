---
title: 活動的安全性考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc49afd-a1c3-4ac7-8b89-11be667221e2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26ea453b24ac3e8df25e7a4da98f27731f3828be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270054"
---
# <a name="security-considerations-for-activities"></a><span data-ttu-id="f368c-102">活動的安全性考量</span><span class="sxs-lookup"><span data-stu-id="f368c-102">Security Considerations for Activities</span></span>
<span data-ttu-id="f368c-103">您在攔截 WCF 配接器時使用的安全性角色，與用於其他 BAM 解決方案的角色相同。</span><span class="sxs-lookup"><span data-stu-id="f368c-103">The security roles you use when intercepting the WCF adapter are the same as those used for other BAM solutions.</span></span> <span data-ttu-id="f368c-104">攔截 WCF 配接器的額外考量包括選取要使用的正確使用者和事件寫入者角色。</span><span class="sxs-lookup"><span data-stu-id="f368c-104">The additional considerations for intercepting the WCF adapter involve selecting the correct user and event writer role to use.</span></span>  
  
 <span data-ttu-id="f368c-105">使用 WCF 服務和 WCF 配接器時，所有與 BAM 相關的資料都會由選取的角色寫入「BAM 主要匯入」資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f368c-105">When using WCF services and the WCF adapter, all BAM-related data is written to the BAM Primary Import database by the selected role.</span></span>  
  
 <span data-ttu-id="f368c-106">您可以透過評估解決方案的情況來選取適當的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="f368c-106">You can select the proper user role configuration by assessing your solution scenario:</span></span>  
  
-   <span data-ttu-id="f368c-107">如果您的解決方案需要各種不同活動追蹤的許多新服務，而且全部以相同的使用者帳戶執行，則較好的方式是使用 BAM_EVENT_WRITER 超級角色寫入攔截的事件。</span><span class="sxs-lookup"><span data-stu-id="f368c-107">If your solution requires many new services that are tracked by many different activities, and are all run under the same user account, it is advantageous to use the BAM_EVENT_WRITER super role to write the intercepted events.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f368c-108">使用者必須加入至 BAM 事件寫入者超級角色。</span><span class="sxs-lookup"><span data-stu-id="f368c-108">Users must be added to the BAM event writer super role.</span></span> <span data-ttu-id="f368c-109">將使用者加入超級角色時，務必記得該使用者將能夠寫入系統中的所有活動。</span><span class="sxs-lookup"><span data-stu-id="f368c-109">When adding a user to the super role it is important to remember that the user will then be able to write to all the activities in the system.</span></span>  
  
-   <span data-ttu-id="f368c-110">如果您的解決方案需要對寫入的事件具有較大的控制權，則應該使用活動專屬的角色。</span><span class="sxs-lookup"><span data-stu-id="f368c-110">If your solution requires greater control of the events written, then you should use activity-specific roles.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f368c-111">針對每項活動，必須將使用者加入活動專屬的事件寫入者角色。</span><span class="sxs-lookup"><span data-stu-id="f368c-111">Users must be added to the activity specific event writer role for each activity.</span></span>  
  
 <span data-ttu-id="f368c-112">如需設定 BAM 事件寫入者角色的詳細資訊，請參閱[如何判斷和設定事件寫入者角色活動](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="f368c-112">For more information about configuring the BAM event writer roles, see [How to Determine and Set Event Writer Roles for Activities](../core/how-to-determine-and-set-event-writer-roles-for-activities.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f368c-113">您必須是「BizTalk 應用程式使用者」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="f368c-113">You must be a member of the BizTalk Application Users group.</span></span>  
  
 <span data-ttu-id="f368c-114">選取設定 BAM WCF 攔截器進行 IIS 下的模擬安全性時要使用的使用者帳戶時，應考慮下列情況：</span><span class="sxs-lookup"><span data-stu-id="f368c-114">When selecting the user account to use when configuring the BAM WCF interceptor for impersonation security under IIS you should consider the following scenarios:</span></span>  
  
-   <span data-ttu-id="f368c-115">自我裝載： 可執行檔，執行您的電腦上，讓 WCF 服務保持開啟。</span><span class="sxs-lookup"><span data-stu-id="f368c-115">Self-Hosted: An executable running on your computer that holds the WCF service open.</span></span>  
  
-   <span data-ttu-id="f368c-116">WCF 配接器： 使用所建立的方案**Biztalk WCF 服務發佈精靈**。</span><span class="sxs-lookup"><span data-stu-id="f368c-116">WCF adapter: Solutions created using the **Biztalk WCF Service Publishing Wizard**.</span></span>  
  
-   <span data-ttu-id="f368c-117">IIS 裝載： 使用 WCF 服務的 IIS 應用程式中裝載的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f368c-117">IIS hosted: A solution hosted in an IIS application using a WCF Service.</span></span>  
  
 <span data-ttu-id="f368c-118">使用下表幫助您識別要使用的帳戶：</span><span class="sxs-lookup"><span data-stu-id="f368c-118">Use the following table to help identify the account to use:</span></span>  
  
|<span data-ttu-id="f368c-119">解決方案類型</span><span class="sxs-lookup"><span data-stu-id="f368c-119">Solution type</span></span>|<span data-ttu-id="f368c-120">要使用的帳戶</span><span class="sxs-lookup"><span data-stu-id="f368c-120">Account to use</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="f368c-121">自我主控</span><span class="sxs-lookup"><span data-stu-id="f368c-121">Self-hosted</span></span>|<span data-ttu-id="f368c-122">用來執行將使服務保持開啟狀態之可執行檔的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f368c-122">The account that is used to run the executable that will hold the service open.</span></span>|  
|<span data-ttu-id="f368c-123">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="f368c-123">WCF adapter</span></span>|<span data-ttu-id="f368c-124">使用 AppPool 識別： 這是 AppPool 與裝載接收位置的 Vroot 相關聯。</span><span class="sxs-lookup"><span data-stu-id="f368c-124">Use the AppPool identity: This is the AppPool associated with the Vroot that houses the receive location.</span></span> <span data-ttu-id="f368c-125">當您使用自動建立此識別**BizTalk WCF 服務發佈精靈**發行網站。</span><span class="sxs-lookup"><span data-stu-id="f368c-125">This identity is created automatically when you use the **BizTalk WCF Service Publishing Wizard** to publish the site.</span></span> <span data-ttu-id="f368c-126">您可以將此視為 IIS 主控解決方案的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="f368c-126">You can consider this a special case of the IIS-hosted solution.</span></span>|  
|<span data-ttu-id="f368c-127">IIS 主控</span><span class="sxs-lookup"><span data-stu-id="f368c-127">IIS-hosted</span></span>|<span data-ttu-id="f368c-128">執行 WCF 服務 VRoot/應用程式的 AppPool 使用者識別。</span><span class="sxs-lookup"><span data-stu-id="f368c-128">The identity of the AppPool user running the WCF service VRoot/Application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f368c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f368c-129">See Also</span></span>  
 [<span data-ttu-id="f368c-130">BAM 攔截器的安全性考量</span><span class="sxs-lookup"><span data-stu-id="f368c-130">Security Considerations for BAM Interceptors</span></span>](../core/security-considerations-for-bam-interceptors.md)