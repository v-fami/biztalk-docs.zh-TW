---
title: 為何為 BAM 撰寫程式碼？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4434f50a-e0a9-45e0-8c68-a059011e1296
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10b8ccb29d95daf8ccdf80d67faef3e50495af04
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="why-write-code-for-bam"></a><span data-ttu-id="ad6ad-103">為何為 BAM 撰寫程式碼？</span><span class="sxs-lookup"><span data-stu-id="ad6ad-103">Why Write Code For BAM?</span></span>
<span data-ttu-id="ad6ad-104">在多數狀況下，您都可以使用 BAM 工具，而不需要撰寫自己的程式碼以執行追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-104">In most circumstances you can use the BAM tools without writing your own code to perform your tracking functions.</span></span> <span data-ttu-id="ad6ad-105">這些工具包括適用於 Excel 的 BAM 增益集、[BAM 管理公用程式]，以及 [追蹤設定檔編輯器] (TPE)。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-105">These tools are the BAM Add-in for Excel, the BAM Management utility, and the Tracking Profile Editor (TPE).</span></span> <span data-ttu-id="ad6ad-106">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 BAM 提供 BizTalk 協調流程和傳訊元件 (管線和連接埠) 的攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-106">BAM in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides interceptors for BizTalk orchestrations and messaging components (pipelines and ports).</span></span> <span data-ttu-id="ad6ad-107">攔截器是一種檢測應用程式的軟體，使其能夠根據組態檔而以一般方式收集資料。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-107">An interceptor is software that instruments an application so that it can collect data in a generic way based on a configuration file.</span></span> <span data-ttu-id="ad6ad-108">您可以使用 [追蹤設定檔編輯器] 來檢測應用程式，以便使用這些攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-108">You can instrument your application to use these interceptors by using the Tracking Profile Editor.</span></span> <span data-ttu-id="ad6ad-109">如需追蹤設定檔編輯器的詳細資訊，請參閱[追蹤設定檔編輯器](../core/tracking-profile-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-109">For more information about the Tracking Profile Editor, see [Tracking Profile Editor](../core/tracking-profile-editor.md).</span></span>  
  
 <span data-ttu-id="ad6ad-110">不過，在兩種主要的案例中，您會發現使用 BAM API 檢測應用程式有很多優點：</span><span class="sxs-lookup"><span data-stu-id="ad6ad-110">There are two primary scenarios, however, in which you will find it advantageous to instrument your application using the BAM APIs:</span></span>  
  
-   <span data-ttu-id="ad6ad-111">您想要監視的主控件沒有 BAM 攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-111">There is no BAM interceptor for the host you intend to monitor.</span></span>  
  
-   <span data-ttu-id="ad6ad-112">應用程式的複雜性不允許內建的攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-112">The built-in interceptor does not allow for the complexity of your application.</span></span>  
  
 <span data-ttu-id="ad6ad-113">沒有內建的攔截器時，您可以使用 BAM **EventStream** Api 來擷取感興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-113">When there is no built-in interceptor, you can use the BAM **EventStream** APIs to capture the events of interest.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad6ad-114">您可以結合 **EventStream** 類別與 **BAMInterceptor** 類別來建立自己的攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-114">You can combine **EventStream** classes with the **BAMInterceptor** class to create your own interceptor.</span></span> <span data-ttu-id="ad6ad-115">The BAM API SDK 範例說明您可以延伸的簡單一般攔截器。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-115">The BAM API SDK sample illustrates a simple generic interceptor that you can extend.</span></span> <span data-ttu-id="ad6ad-116">藉由建構自己的攔截器，您可以檢測多個相似的處理序，而不需要為每個應用程式撰寫新的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-116">By constructing your own interceptor you can instrument a number of similar processes without writing new code for each application.</span></span> <span data-ttu-id="ad6ad-117">若要檢視 BAM API SDK 範例，請參閱[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6ad-117">To view the BAM API SDK sample, see [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6ad-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad6ad-118">See Also</span></span>  
 [<span data-ttu-id="ad6ad-119">實作 BAM 解決方案</span><span class="sxs-lookup"><span data-stu-id="ad6ad-119">Implementing BAM Solutions</span></span>](../core/implementing-bam-solutions.md)