---
title: "監控主控件執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7c6b80-7371-46ea-bf9c-82acb22012a3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 561c40e791d82b28060a45ada51bebed4cd784c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-host-instances"></a>監控主控件執行個體
本主題描述使用 Microsoft System Center Operations Manager 監視 BizTalk 主控件執行個體。  
  
## <a name="using-threshold-rules-to-monitor-health"></a>使用監視健全狀況的臨界值規則  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理封包加入了效能閾值規則，提供 BizTalk 主控件的健全狀況的完整檢視。 提供的閾值規則有兩個類型：  
  
-   以一般方式 （例如，所有的 MessageBox 資料庫以及所有 BizTalk 主控件） 套用的規則。  
  
-   專屬於特定的 BizTalk 主控件的規則。  
  
 一般規則會監控所有 BizTalk 主控件根據通用閾值。 例如，規則監控 HostQ 大小監視根據通用閾值的所有 BizTalk 主控件工作佇列。 如果有三個不同的主控件，其所有的工作佇列監視由相同的規則，並且任何主控件工作佇列超越通用閾值時，會發生的警示。  
  
 BizTalk 主控件專用規則可讓您針對不同的主控件設定不同的臨界值。 例如，規則監控 HostQ 大小 – BizTalkServerApplication 是監視工作佇列的 biztalkserverapplication 主控件的主控件專用規則。 在此範例中，您可以定義特定效能計數器執行個體的特定 Operations Manager 提供者，並在閾值規則中使用該提供者。 因為這些規則是特定的主機，您必須定義特定規則加入每個新建立的主機。  
  
 BizTalk 主控件專用規則提供為建立規則的範本規則是適用於您的環境。 依照預設，所有的閾值監控規則會停用：  
  
-   您應該在您的環境特有的閾值設定一般規則。  
  
-   您應該建立 BizTalk 主控件專用規則根據範本規則和適當的臨界值。  
  
## <a name="monitoring-biztalk-host-instances"></a>監控 BizTalk 主控件執行個體  
 以特定 BizTalk 主控件為目標的規則是從監視的觀點來看更有彈性。 所有 biztalkserverapplication 主控件中提供的監視規則的臨界值[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理組件都是範本規則。 若要使用這些規則，您應該使用在 Operations Manager 系統管理員主控台：  
  
-   在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 規則群組中建立範本規則的複本，然後將它重新命名。  
  
-   建立新的 Operations Manager 提供者的 BizTalk 主控件特定的效能計數器執行個體。  
  
-   修改規則所用的 Operations Manager 提供者，並指向新的專案。  
  
 假設您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝 BizTalk 主控件 ReceiveHost，您想要監視為此主控件的主控件佇列大小。 在此情況下，您應該建立 Operations Manager 提供者，根據 BizTalk 主控件佇列大小的效能計數器的 ReceiveHost 執行個體。 您也應該針對您的環境適當調整規則中的閾值。  
  
 如果您使用特定主機的閾值監控規則，您應該停用一般監控規則。 這可以避免多餘的警示。  
  
## <a name="see-also"></a>另請參閱  
 [監控 BizTalk Server 與 System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)