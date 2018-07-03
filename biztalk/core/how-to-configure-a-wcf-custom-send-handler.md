---
title: 如何設定 Wcf-custom 傳送處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00758b87-dffb-488b-9cf3-564d0ccd5938
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a80ec79dd839c4a7e82d17e3b559abf6cba89a6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996831"
---
# <a name="how-to-configure-a-wcf-custom-send-handler"></a><span data-ttu-id="f088d-102">如何設定 WCF-Custom 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="f088d-102">How to Configure a WCF-Custom Send Handler</span></span>
<span data-ttu-id="f088d-103">如果您希望 [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] 向 machine.config 以外的位置查詢自訂行為延伸模組，您必須設定傳送處理常式屬性。</span><span class="sxs-lookup"><span data-stu-id="f088d-103">You must configure the send handler properties if you want the [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] to look up the custom behavior extensions from locations other than machine.config.</span></span>  
  
## <a name="why-should-wcf-custom-adapter-look-up-custom-behavior-extensions-from-locations-other-than-machineconfig"></a><span data-ttu-id="f088d-104">為什麼 WCF-Custom 配接器應向 machine.config 以外的位置查詢自訂行為延伸模組？</span><span class="sxs-lookup"><span data-stu-id="f088d-104">Why Should WCF-Custom Adapter Look up Custom Behavior Extensions from Locations Other than machine.config?</span></span>  
 <span data-ttu-id="f088d-105">所使用的自訂行為延伸模組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 machine.config 中註冊。載入行為延伸模組之前[!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)]尋找 machine.config 中的行為延伸模組。不過，machine.config 適合用來儲存特定電腦上執行的所有應用程式需要的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="f088d-105">Custom behavior extensions used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is registered in the machine.config. Before loading the behavior extensions, the [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] looks for the behavior extensions in machine.config. However, machine.config is ideally used to store configuration information that is required across all applications running on a particular computer.</span></span> <span data-ttu-id="f088d-106">另一方面，需要 WCF 自訂行為延伸模組的可能只有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而不是電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="f088d-106">On the other hand, WCF custom behavior extensions may be required only by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and not by all the applications running on the computer.</span></span> <span data-ttu-id="f088d-107">因此，雖然在 machine.config 中儲存自訂行延伸模組可達到目的，但這並不是最佳位置。</span><span class="sxs-lookup"><span data-stu-id="f088d-107">So, while storing the custom behavior extensions in machine.config serves the purpose, it is not the most optimal location.</span></span>  
  
 <span data-ttu-id="f088d-108">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，配接器處理常式屬性提供了另一個可讓 [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] 查詢自訂行為延伸模組的位置。</span><span class="sxs-lookup"><span data-stu-id="f088d-108">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the adapter handler properties provide an additional location from which the [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] can look up the custom behavior extensions.</span></span> <span data-ttu-id="f088d-109">請注意，這並不會取代 machine.config 中已有的行為延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f088d-109">Note that this does not replace the behavior extensions already available in machine.config.</span></span>  
  
### <a name="additional-considerations"></a><span data-ttu-id="f088d-110">其他考量</span><span class="sxs-lookup"><span data-stu-id="f088d-110">Additional Considerations</span></span>  
 <span data-ttu-id="f088d-111">在設定 WCF-Custom 傳送處理常式屬性時，請注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="f088d-111">Keep the following points in mind while configuring the WCF-Custom send handler properties:</span></span>  
  
-   <span data-ttu-id="f088d-112">自訂行為延伸模組必須出現在 machine.config 或配接器處理常式屬性中。</span><span class="sxs-lookup"><span data-stu-id="f088d-112">The custom behavior extensions must be available either in the machine.config or in the adapter handler properties.</span></span> <span data-ttu-id="f088d-113">這兩個位置的自訂行為延伸模組不能重複。</span><span class="sxs-lookup"><span data-stu-id="f088d-113">The custom behavior extensions must not be duplicated at both locations.</span></span>  
  
-   <span data-ttu-id="f088d-114">如果自訂行為延伸模組已出現在 machine.config 中，而您嘗試在配接器處理常式屬性中設定同一個延伸模組，則當您嘗試設定屬性時會立即出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="f088d-114">If the custom behavior extension is already available in the machine.config and you try to set the same behavior extension for the adapter handler properties, you get an error as soon as you try to set the property.</span></span>  
  
-   <span data-ttu-id="f088d-115">如果配接器處理常式屬性中已經設定自訂行為延伸模組，而您又以同一個行為延伸模組來更新 machine.config，即會出現執行階段錯誤並記錄在事件日誌中。</span><span class="sxs-lookup"><span data-stu-id="f088d-115">If the custom behavior extension is already set for the adapter handler properties and you then update the machine.config with the same behavior extension, you will get a runtime error and it is also logged in the event log.</span></span>  
  
-   <span data-ttu-id="f088d-116">自訂行為延伸模組中參考的組件必須存在全域組件快取 (GAC) 中，您才能設定配接器處理常式屬性。</span><span class="sxs-lookup"><span data-stu-id="f088d-116">The assemblies referred in the custom behavior extension must be present in the Global Assembly Cache (GAC) before you set the adapter handler properties.</span></span>  
  
## <a name="configuring-the-adapter-handler-properties"></a><span data-ttu-id="f088d-117">設定配接器處理常式屬性</span><span class="sxs-lookup"><span data-stu-id="f088d-117">Configuring the Adapter Handler Properties</span></span>  
 <span data-ttu-id="f088d-118">使用本主題的程序來設定 WCF-Custom 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="f088d-118">Use the procedure in this topic to configure a WCF-Custom send handler.</span></span>  
  
#### <a name="to-configure-the-adapter-handler-properties"></a><span data-ttu-id="f088d-119">若要設定配接器處理常式屬性</span><span class="sxs-lookup"><span data-stu-id="f088d-119">To configure the adapter handler properties</span></span>  
  
1. <span data-ttu-id="f088d-120">在 BizTalk 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="f088d-120">In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2. <span data-ttu-id="f088d-121">在展開的配接器清單中，按一下**Wcf-custom**，在右窗格以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f088d-121">In the expanded adapter list, click **WCF-Custom**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="f088d-122">在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取主控件與傳送處理常式將會產生關聯，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f088d-122">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="f088d-123">在  **Wcf-custom 傳輸屬性**對話方塊的  **WCF 延伸模組**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f088d-123">In the **WCF-Custom Transport Properties** dialog box, on the **WCF Extensions** tab, do the following:</span></span>  
  
   |<span data-ttu-id="f088d-124">使用</span><span class="sxs-lookup"><span data-stu-id="f088d-124">Use this</span></span>|<span data-ttu-id="f088d-125">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="f088d-125">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="f088d-126">**匯入**</span><span class="sxs-lookup"><span data-stu-id="f088d-126">**Import**</span></span>|<span data-ttu-id="f088d-127">匯入含有 WCF 自訂行為延伸模組的 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="f088d-127">Imports a WCF configuration file with WCF custom behavior extensions.</span></span> <span data-ttu-id="f088d-128">按一下此按鈕會開啟**匯入 WCF 組態**對話方塊，即可瀏覽並尋找 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="f088d-128">Clicking this button opens the **Import WCF configuration** dialog box to browse and locate a WCF configuration file.</span></span> <span data-ttu-id="f088d-129">請注意，此檔案應為有效的 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="f088d-129">Note that the file should be a valid WCF configuration file.</span></span> <span data-ttu-id="f088d-130">WCF 組態結構描述的詳細資訊，請參閱 「 Windows Communication Foundation 組態結構描述 >，網址[ http://go.microsoft.com/fwlink/?LinkId=163953 ](http://go.microsoft.com/fwlink/?LinkId=163953)。</span><span class="sxs-lookup"><span data-stu-id="f088d-130">For more information about WCF configuration schema, see “Windows Communication Foundation Configuration Schema” at [http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953).</span></span>|  
   |<span data-ttu-id="f088d-131">**匯出**</span><span class="sxs-lookup"><span data-stu-id="f088d-131">**Export**</span></span>|<span data-ttu-id="f088d-132">將 WCF 自訂行為延伸模組匯出到 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="f088d-132">Exports the WCF custom behavior extension to a WCF configuration file.</span></span> <span data-ttu-id="f088d-133">按一下此按鈕會開啟**匯出 WCF 組態**對話方塊，即可瀏覽與儲存 WCF 組態檔。</span><span class="sxs-lookup"><span data-stu-id="f088d-133">Clicking this button opens the **Export WCF configuration** dialog box to browse and save the WCF configuration file.</span></span>|  
   |<span data-ttu-id="f088d-134">**Clear**</span><span class="sxs-lookup"><span data-stu-id="f088d-134">**Clear**</span></span>|<span data-ttu-id="f088d-135">從配接器處理常式屬性中清除現有的 WCF 自訂行為延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f088d-135">Clears the existing WCF custom behavior extension from the adapter handler properties.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f088d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f088d-136">See Also</span></span>  
 [<span data-ttu-id="f088d-137">設定 WCF-Custom 配接器</span><span class="sxs-lookup"><span data-stu-id="f088d-137">Configuring the WCF-Custom Adapter</span></span>](../core/configuring-the-wcf-custom-adapter.md)