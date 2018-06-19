---
title: 匯入或使用 BTSTask 匯出 BizTalk 設定 |Microsoft 文件
description: 將設定從環境移到另一個 BizTalk Server 中使用 ImportSettings 或 ExportSettings BTSTask 命令
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3fdd8c9-3534-4c11-8acc-6cb6f5bf0989
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99aecaea767133fc5f3cb77d38dc174b09733674
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255142"
---
# <a name="use-btstask-to-import-or-export-biztalk-settings"></a><span data-ttu-id="db187-103">使用 BTSTask 匯入或匯出 BizTalk 設定</span><span class="sxs-lookup"><span data-stu-id="db187-103">Use BTSTask to import or export BizTalk settings</span></span>

## <a name="overview"></a><span data-ttu-id="db187-104">概觀</span><span class="sxs-lookup"><span data-stu-id="db187-104">Overview</span></span>
<span data-ttu-id="db187-105">您可以使用 BTSTask 命令列公用程式，匯出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中的設定，再將該設定匯入到其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，進而縮短完成解決方案所需的整體時間。</span><span class="sxs-lookup"><span data-stu-id="db187-105">Using the BTSTask command-line utility, you can export the settings from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and import them to another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, thereby reducing the overall time-to-solution.</span></span> <span data-ttu-id="db187-106">當系統管理員會試著在臨時環境中調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能，並會在達成想要的結果時將設定匯入實際執行環境的情況下，這種方式就特別有用。</span><span class="sxs-lookup"><span data-stu-id="db187-106">This is especially useful in scenarios where the administrators try to tune [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance in a staging environment, and upon achieving the desired results, they can import the settings into a production environment.</span></span> 

<span data-ttu-id="db187-107">本主題列出的步驟，匯入或從一個環境的 BizTalk Server 設定匯出到另一個使用**BTSTask.exe**。</span><span class="sxs-lookup"><span data-stu-id="db187-107">This topic lists the steps to import or export the BizTalk Server settings from one environment to another using **BTSTask.exe**.</span></span>  


## <a name="import-biztalk-settings"></a><span data-ttu-id="db187-108">匯入 BizTalk 設定</span><span class="sxs-lookup"><span data-stu-id="db187-108">Import BizTalk settings</span></span> 
> [!IMPORTANT]
>  <span data-ttu-id="db187-109">若要從某個環境匯入 BizTalk 設定，您必須已經將這些設定匯出並儲存成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="db187-109">To import the BizTalk settings from a certain environment, you should have already exported and saved those settings in an XML file.</span></span> <span data-ttu-id="db187-110">如需有關匯出設定的詳細資訊，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)或**使用 BTSTask 匯出 BizTalk 設定**（在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="db187-110">For more information about exporting the settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) or **Export BizTalk Settings Using BTSTask** (in this topic).</span></span>  
  
 <span data-ttu-id="db187-111">透過匯入 XML 檔案，您可以將必要的 BizTalk Server 設定複製到目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="db187-111">By importing the XML file, you can replicate the required BizTalk Server settings on the target machine.</span></span> <span data-ttu-id="db187-112">使用**BTSTask.exe**，您可以匯入群組、 主機和主控件執行個體的設定，並將屬性相互對應。</span><span class="sxs-lookup"><span data-stu-id="db187-112">Using the **BTSTask.exe**, you can import the Group, Host, and Host Instance settings and map the properties of one to another.</span></span> <span data-ttu-id="db187-113">以下是匯入設定的必要假設：</span><span class="sxs-lookup"><span data-stu-id="db187-113">Following are the necessary assumptions for importing the settings:</span></span>  
  
-   <span data-ttu-id="db187-114">您可以將 BizTalk Server 設定匯入到類似的拓撲。</span><span class="sxs-lookup"><span data-stu-id="db187-114">You can import the BizTalk Server settings across similar topologies.</span></span>  
  
-   <span data-ttu-id="db187-115">您應該要能將來源與目的地的「主控件」和「主控件執行個體」相對應。</span><span class="sxs-lookup"><span data-stu-id="db187-115">You should be able to map the source Host and Host Instances to the destination counterparts.</span></span>  
  
-   <span data-ttu-id="db187-116">目的環境與來源環境有相似的硬體 (如果不完全相同)。</span><span class="sxs-lookup"><span data-stu-id="db187-116">The destination environment has hardware similar (if not identical) to the source environment.</span></span> <span data-ttu-id="db187-117">這很重要，因為部分設定的運作要仰賴基礎硬體。</span><span class="sxs-lookup"><span data-stu-id="db187-117">This is essential as some of the settings depend on the underlying hardware.</span></span>  
  
### <a name="importsettings-command"></a><span data-ttu-id="db187-118">ImportSettings 命令</span><span class="sxs-lookup"><span data-stu-id="db187-118">ImportSettings command</span></span> 
 <span data-ttu-id="db187-119">您可以使用**ImportSettings** BTSTask 命令從來源環境的 BizTalk Server 設定匯入到目的地環境。</span><span class="sxs-lookup"><span data-stu-id="db187-119">You can use the **ImportSettings** BTSTask command to import BizTalk Server settings from the source environment to destination environment.</span></span> <span data-ttu-id="db187-120">請參閱[ImportSettings 命令](../core/importsettings-command.md)的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="db187-120">See [ImportSettings Command](../core/importsettings-command.md) for specific details.</span></span>  
  
 <span data-ttu-id="db187-121">您可以定義來源主控件到目的地主控件的對應和/或來源主控件執行個體到目的地主控件執行個體的對應，如下所示：</span><span class="sxs-lookup"><span data-stu-id="db187-121">You can define the mapping from a source host to a destination host and/or a source host instance to a destination host instance as shown:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SettingsMap>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <HostMappings>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="BizTalkServerApplication">  
  <DestinationHosts>BizTalkServerApplication</DestinationHosts>   
  </SourceHost>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="BizTalkServerIsolatedHost">  
  <DestinationHosts>BizTalkServerIsolatedHost</DestinationHosts>   
  </SourceHost>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="Host1">  
  <DestinationHosts>Host2</DestinationHosts>   
  </SourceHost>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="Host2">  
  <DestinationHosts>Host1;Host3;Host4;Host5</DestinationHosts>   
  </SourceHost>  
  </HostMappings>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <HostInstanceMappings>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHostInstance Name="BizTalkServerApplication:COMPUTER_NAME1">  
  <DestinationHostInstances>BizTalkServerApplication:COMPUTER_NAME2</DestinationHostInstances>   
  </SourceHostInstance>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHostInstance Name="Host1:COMPUTER_NAME1">  
  <DestinationHostInstances>Host2:COMPUTER_NAME2;Host3:COMPUTER_NAME3;Host4:COMPUTER_NAME4;Host5:COMPUTER_NAME5</DestinationHostInstances>   
  </SourceHostInstance>  
  </HostInstanceMappings>  
  </SettingsMap>  
  
```  
  
 <span data-ttu-id="db187-122">在對應檔案中，輸入主控件執行個體做為 'Hostname: Machinename'。</span><span class="sxs-lookup"><span data-stu-id="db187-122">In a map file, enter a host instance as 'HostName:MachineName'.</span></span> <span data-ttu-id="db187-123">例如："Host1:Server1" 表示 'Host1' 主控件的執行個體，它會在 'Server1"電腦上執行 (或存在)。</span><span class="sxs-lookup"><span data-stu-id="db187-123">For example: "Host1:Server1" means the instance of host 'Host1' which is running (or present) on machine 'Server1".</span></span>  
  
 <span data-ttu-id="db187-124">若要輸入 1: n 來源至目的地的對應，請使用分號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="db187-124">To enter 1:n source to destination mappings, use a semicolon-separated list.</span></span> <span data-ttu-id="db187-125">例如：</span><span class="sxs-lookup"><span data-stu-id="db187-125">For example:</span></span>  
  
```  
SourceHost Name="SourceHost1"   
......DestinationHosts   
............DestHost1;DestHost2;DestHost3   
....../DestinationHosts   
/SourceHost  
```  
  
 <span data-ttu-id="db187-126">只有已建立相對應之主控件對應的主控件執行個體才能對應。</span><span class="sxs-lookup"><span data-stu-id="db187-126">Only those host-instances can be mapped for which the corresponding host mapping has also been created.</span></span> <span data-ttu-id="db187-127">如果在主控件對應中 'SourceHost1' 已對應至 'DestinationHost1'，則 'DestinationHost1' 的執行個體 (若有的話) 只能對應至 'SourceHost1' 的執行個體 (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="db187-127">If 'SourceHost1' has been mapped to 'DestinationHost1' in host mappings, the instances (if any) of 'DestinationHost1' can be mapped only to the instances (if any) of 'SourceHost1'.</span></span> <span data-ttu-id="db187-128">[UI 匯入精靈] 會注意此條件約束。</span><span class="sxs-lookup"><span data-stu-id="db187-128">The UI Import Wizard takes care of this constraint.</span></span> <span data-ttu-id="db187-129">您需要在對應檔中明確撰寫它。</span><span class="sxs-lookup"><span data-stu-id="db187-129">You would need to explicitly write it in the map file.</span></span>  


## <a name="export-biztalk-settings"></a><span data-ttu-id="db187-130">匯出 BizTalk 設定</span><span class="sxs-lookup"><span data-stu-id="db187-130">Export BizTalk settings</span></span>  

<span data-ttu-id="db187-131">有幾種方式匯出 BizTalk 設定：</span><span class="sxs-lookup"><span data-stu-id="db187-131">There are a couple of ways to export the BizTalk settings:</span></span> 

1. <span data-ttu-id="db187-132">使用**ExportSettings** BTSTask 命令，將來源環境的 BizTalk Server 設定匯出至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="db187-132">Use the **ExportSettings** BTSTask command to export the BizTalk Server settings of the source environment to an XML file.</span></span> <span data-ttu-id="db187-133">請參閱[ExportSettings 命令](../core/exportsettings-command.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="db187-133">See [ExportSettings Command](../core/exportsettings-command.md) for more details.</span></span>  

2.  <span data-ttu-id="db187-134">在 BizTalk Server 管理 中使用設定儀表板。</span><span class="sxs-lookup"><span data-stu-id="db187-134">Use the Settings Dashboard in BizTalk Server Administration.</span></span> <span data-ttu-id="db187-135">請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)的步驟。</span><span class="sxs-lookup"><span data-stu-id="db187-135">See [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) for the steps.</span></span>

 
> [!TIP]
>  <span data-ttu-id="db187-136">如需如何將 XML 檔案中的 BizTalk Server 設定套用至目標環境的資訊，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。</span><span class="sxs-lookup"><span data-stu-id="db187-136">For information about how the BizTalk Server settings in an XML file are applied to the target environment, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="db187-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db187-137">See Also</span></span>  
 [<span data-ttu-id="db187-138">自動化 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="db187-138">Automate BizTalk Server Performance Tuning</span></span>](../core/automating-biztalk-server-performance-tuning.md)