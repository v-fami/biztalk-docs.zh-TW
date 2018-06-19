---
title: 如何設定 Wcf-customisolated 接收處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e90add2-1a5e-4509-a98c-b3c297b4213f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00e52daaaefc3f85537dc3c51f8700da30b74876
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248534"
---
# <a name="how-to-configure-a-wcf-customisolated-receive-handler"></a><span data-ttu-id="ed376-102">如何設定 Wcf-customisolated 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="ed376-102">How to Configure a WCF-CustomIsolated Receive Handler</span></span>
<span data-ttu-id="ed376-103">如果您想要查閱 machine.config 以外的位置的自訂行為延伸模組 Wcf-customisolated 配接器，您必須設定接收處理常式屬性。</span><span class="sxs-lookup"><span data-stu-id="ed376-103">You must configure the receive handler properties if you want the WCF-CustomIsolated adapter to lookup the custom behavior extension from locations other than machine.config.</span></span>  
  
## <a name="why-should-wcf-customisolated-adapter-look-up-custom-behavior-extensions-from-locations-other-than-machineconfig"></a><span data-ttu-id="ed376-104">為什麼應該 Wcf-customisolated 配接器查詢自訂行為延伸模組 machine.config 以外的位置？</span><span class="sxs-lookup"><span data-stu-id="ed376-104">Why Should WCF-CustomIsolated Adapter Look up Custom Behavior Extensions from Locations Other than machine.config?</span></span>  
 <span data-ttu-id="ed376-105">所使用的自訂行為延伸模組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]machine.config 中註冊。然後再載入行為延伸模組，Wcf-customisolated 配接器會尋找在 machine.config 中的行為延伸模組。不過，machine.config 適合用來儲存特定電腦上執行的所有應用程式需要的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="ed376-105">Custom behavior extensions used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are registered in the machine.config. Before loading the behavior extensions, the WCF-CustomIsolated adapter looks for the behavior extensions in machine.config. However, machine.config is ideally used to store configuration information that is required across all applications running on a particular computer.</span></span> <span data-ttu-id="ed376-106">另一方面，需要 WCF 自訂行為延伸模組的可能只有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而不是電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed376-106">On the other hand, WCF custom behavior extensions may be required only by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and not by all the applications running on the computer.</span></span> <span data-ttu-id="ed376-107">因此，雖然在 machine.config 中儲存自訂行延伸模組可達到目的，但這並不是最佳位置。</span><span class="sxs-lookup"><span data-stu-id="ed376-107">So, while storing the custom behavior extensions in machine.config serves the purpose, it is not the most optimal location.</span></span>  
  
 <span data-ttu-id="ed376-108">與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，配接器處理常式屬性提供其他從中 Wcf-customisolated 配接器可以查詢自訂行為延伸模組的位置。</span><span class="sxs-lookup"><span data-stu-id="ed376-108">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the adapter handler properties provide an additional location from which the WCF-CustomIsolated adapter can look up the custom behavior extensions.</span></span> <span data-ttu-id="ed376-109">請注意，這並不會取代 machine.config 中已有的行為延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ed376-109">Note that this does not replace the behavior extensions already available in machine.config.</span></span>  
  
### <a name="additional-considerations"></a><span data-ttu-id="ed376-110">其他考量</span><span class="sxs-lookup"><span data-stu-id="ed376-110">Additional Considerations</span></span>  
 <span data-ttu-id="ed376-111">保留下列幾點點時設定 Wcf-customisolated 接收處理常式屬性：</span><span class="sxs-lookup"><span data-stu-id="ed376-111">Keep the following points in mind while configuring the WCF-CustomIsolated receive handler properties:</span></span>  
  
-   <span data-ttu-id="ed376-112">自訂行為延伸模組必須出現在 machine.config 或配接器處理常式屬性中。</span><span class="sxs-lookup"><span data-stu-id="ed376-112">The custom behavior extensions must be available either in the machine.config or in the adapter handler properties.</span></span> <span data-ttu-id="ed376-113">這兩個位置的自訂行為延伸模組不能重複。</span><span class="sxs-lookup"><span data-stu-id="ed376-113">The custom behavior extensions must not be duplicated at both locations.</span></span>  
  
-   <span data-ttu-id="ed376-114">如果自訂行為延伸模組已出現在 machine.config 中，而您嘗試在配接器處理常式屬性中設定同一個延伸模組，則當您嘗試設定屬性時會立即出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed376-114">If the custom behavior extension is already available in the machine.config and you try to set the same behavior extension for the adapter handler properties, you get an error as soon as you try to set the property.</span></span>  
  
-   <span data-ttu-id="ed376-115">如果配接器處理常式屬性中已經設定自訂行為延伸模組，而您又以同一個行為延伸模組來更新 machine.config，即會出現執行階段錯誤並記錄在事件日誌中。</span><span class="sxs-lookup"><span data-stu-id="ed376-115">If the custom behavior extension is already set for the adapter handler properties and you then update the machine.config with the same behavior extension, you will get a runtime error and it is also logged in the event log.</span></span> <span data-ttu-id="ed376-116">接收位置同時會遭停用。</span><span class="sxs-lookup"><span data-stu-id="ed376-116">The receive location is also disabled.</span></span>  
  
-   <span data-ttu-id="ed376-117">自訂行為延伸模組中參考的組件必須存在全域組件快取 (GAC) 中，您才能設定配接器處理常式屬性。</span><span class="sxs-lookup"><span data-stu-id="ed376-117">The assemblies referred in the custom behavior extension must be present in the Global Assembly Cache (GAC) before you set the adapter handler properties.</span></span>  
  
## <a name="configuring-the-adapter-handler-properties"></a><span data-ttu-id="ed376-118">設定配接器處理常式屬性</span><span class="sxs-lookup"><span data-stu-id="ed376-118">Configuring the Adapter Handler Properties</span></span>  
 <span data-ttu-id="ed376-119">使用下列程序來設定 Wcf-customisolated 接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="ed376-119">Use the following procedure to configure a WCF-CustomIsolated receive handler.</span></span>  
  
#### <a name="to-configure-the-adapter-handler-properties"></a><span data-ttu-id="ed376-120">若要設定配接器處理常式屬性</span><span class="sxs-lookup"><span data-stu-id="ed376-120">To configure the adapter handler properties</span></span>  
  
1.  <span data-ttu-id="ed376-121">在 BizTalk 管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="ed376-121">In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="ed376-122">在展開的配接器清單中，按一下  **Wcf-customisolated**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ed376-122">In the expanded adapter list, click **WCF-CustomIsolated**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ed376-123">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯，接收處理常式的主機，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ed376-123">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="ed376-124">在**Wcf-customisolated 傳輸屬性**對話方塊**WCF 延伸模組**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ed376-124">In the **WCF-CustomIsolated Transport Properties** dialog box, on the **WCF Extensions** tab, do the following:</span></span>  
  
    |<span data-ttu-id="ed376-125">使用</span><span class="sxs-lookup"><span data-stu-id="ed376-125">Use this</span></span>|<span data-ttu-id="ed376-126">動作</span><span class="sxs-lookup"><span data-stu-id="ed376-126">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ed376-127">**匯入**</span><span class="sxs-lookup"><span data-stu-id="ed376-127">**Import**</span></span>|<span data-ttu-id="ed376-128">匯入含有 WCF 自訂行為延伸模組的 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed376-128">Imports a WCF configuration file with WCF custom behavior extensions.</span></span> <span data-ttu-id="ed376-129">按一下此按鈕會開啟**匯入 WCF 組態**對話方塊，即可瀏覽並尋找 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed376-129">Clicking this button opens the **Import WCF configuration** dialog box to browse and locate a WCF configuration file.</span></span> <span data-ttu-id="ed376-130">請注意，此檔案應為有效的 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed376-130">Note that the file should be a valid WCF configuration file.</span></span> <span data-ttu-id="ed376-131">如需 WCF 組態結構描述的詳細資訊，請參閱 「 Windows Communication Foundation 組態結構描述 」 在[http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953)。</span><span class="sxs-lookup"><span data-stu-id="ed376-131">For more information about WCF configuration schema, see “Windows Communication Foundation Configuration Schema” at [http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953).</span></span>|  
    |<span data-ttu-id="ed376-132">**匯出**</span><span class="sxs-lookup"><span data-stu-id="ed376-132">**Export**</span></span>|<span data-ttu-id="ed376-133">將 WCF 自訂行為延伸模組匯出到 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed376-133">Exports the WCF custom behavior extension to a WCF configuration file.</span></span> <span data-ttu-id="ed376-134">按一下此按鈕會開啟**匯出 WCF 組態**對話方塊，即可瀏覽與儲存 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed376-134">Clicking this button opens the **Export WCF configuration** dialog box to browse and save the WCF configuration file.</span></span>|  
    |<span data-ttu-id="ed376-135">**Clear**</span><span class="sxs-lookup"><span data-stu-id="ed376-135">**Clear**</span></span>|<span data-ttu-id="ed376-136">從配接器處理常式屬性中清除現有的 WCF 自訂行為延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ed376-136">Clears the existing WCF custom behavior extension from the adapter handler properties.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed376-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed376-137">See Also</span></span>  
 [<span data-ttu-id="ed376-138">設定 Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="ed376-138">Configuring the WCF-CustomIsolated Adapter</span></span>](../core/configuring-the-wcf-customisolated-adapter.md)