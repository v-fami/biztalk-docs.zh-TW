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
# <a name="use-btstask-to-import-or-export-biztalk-settings"></a>使用 BTSTask 匯入或匯出 BizTalk 設定

## <a name="overview"></a>概觀
您可以使用 BTSTask 命令列公用程式，匯出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中的設定，再將該設定匯入到其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，進而縮短完成解決方案所需的整體時間。 當系統管理員會試著在臨時環境中調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能，並會在達成想要的結果時將設定匯入實際執行環境的情況下，這種方式就特別有用。 

本主題列出的步驟，匯入或從一個環境的 BizTalk Server 設定匯出到另一個使用**BTSTask.exe**。  


## <a name="import-biztalk-settings"></a>匯入 BizTalk 設定 
> [!IMPORTANT]
>  若要從某個環境匯入 BizTalk 設定，您必須已經將這些設定匯出並儲存成 XML 檔案。 如需有關匯出設定的詳細資訊，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)或**使用 BTSTask 匯出 BizTalk 設定**（在本主題中）。  
  
 透過匯入 XML 檔案，您可以將必要的 BizTalk Server 設定複製到目標電腦上。 使用**BTSTask.exe**，您可以匯入群組、 主機和主控件執行個體的設定，並將屬性相互對應。 以下是匯入設定的必要假設：  
  
-   您可以將 BizTalk Server 設定匯入到類似的拓撲。  
  
-   您應該要能將來源與目的地的「主控件」和「主控件執行個體」相對應。  
  
-   目的環境與來源環境有相似的硬體 (如果不完全相同)。 這很重要，因為部分設定的運作要仰賴基礎硬體。  
  
### <a name="importsettings-command"></a>ImportSettings 命令 
 您可以使用**ImportSettings** BTSTask 命令從來源環境的 BizTalk Server 設定匯入到目的地環境。 請參閱[ImportSettings 命令](../core/importsettings-command.md)的特定詳細資料。  
  
 您可以定義來源主控件到目的地主控件的對應和/或來源主控件執行個體到目的地主控件執行個體的對應，如下所示：  
  
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
  
 在對應檔案中，輸入主控件執行個體做為 'Hostname: Machinename'。 例如："Host1:Server1" 表示 'Host1' 主控件的執行個體，它會在 'Server1"電腦上執行 (或存在)。  
  
 若要輸入 1: n 來源至目的地的對應，請使用分號分隔的清單。 例如：  
  
```  
SourceHost Name="SourceHost1"   
......DestinationHosts   
............DestHost1;DestHost2;DestHost3   
....../DestinationHosts   
/SourceHost  
```  
  
 只有已建立相對應之主控件對應的主控件執行個體才能對應。 如果在主控件對應中 'SourceHost1' 已對應至 'DestinationHost1'，則 'DestinationHost1' 的執行個體 (若有的話) 只能對應至 'SourceHost1' 的執行個體 (若有的話)。 [UI 匯入精靈] 會注意此條件約束。 您需要在對應檔中明確撰寫它。  


## <a name="export-biztalk-settings"></a>匯出 BizTalk 設定  

有幾種方式匯出 BizTalk 設定： 

1. 使用**ExportSettings** BTSTask 命令，將來源環境的 BizTalk Server 設定匯出至 XML 檔案。 請參閱[ExportSettings 命令](../core/exportsettings-command.md)如需詳細資訊。  

2.  在 BizTalk Server 管理 中使用設定儀表板。 請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)的步驟。

 
> [!TIP]
>  如需如何將 XML 檔案中的 BizTalk Server 設定套用至目標環境的資訊，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。 
  
## <a name="see-also"></a>另請參閱  
 [自動化 BizTalk Server 效能調整](../core/automating-biztalk-server-performance-tuning.md)