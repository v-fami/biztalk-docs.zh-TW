---
title: 監控主控件執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7c6b80-7371-46ea-bf9c-82acb22012a3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91ad5ec158466db6716b515fe3d34ae76c4cde0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003335"
---
# <a name="monitoring-host-instances"></a>監控主控件執行個體
本主題說明使用 Microsoft System Center Operations Manager 監視 BizTalk 主控件執行個體。  
  
## <a name="using-threshold-rules-to-monitor-health"></a>使用臨界值規則來監視健康情況  
 BizTalk Server 管理組件會併入效能閾值規則，提供 BizTalk 主控件的健全狀況的完整檢視。 提供的閾值規則有兩個類型：  
  
- 以一般方式 （例如，所有 BizTalk 主控件以及所有的 MessageBox 資料庫） 所套用的規則。  
  
- 專屬於特定的 BizTalk 主控件的規則。  
  
  一般規則會監控根據通用閾值的所有 BizTalk 主控件。 例如，規則監控 HostQ 大小會監視根據通用閾值的所有 BizTalk 主控件工作佇列。 如果有三個不同的主控件，所有工作佇列由相同的規則，來都監視和警示發生時任何主控件工作佇列超越通用閾值。  
  
  BizTalk 主控件特有規則可讓您針對不同的主控件設定不同的臨界值。 例如，規則監控 HostQ 大小 – BizTalkServerApplication 是監控 biztalkserverapplication 主控件工作佇列的主控件特有規則。 在此範例中，您可以定義特定的效能計數器執行個體的特定 Operations Manager 提供者和臨界值規則中使用該提供者。 因為這些規則是主控件特有的您必須在每個新建立的主控件中定義特定的規則。  
  
  當建立規則的範本規則是適用於您的環境中，會提供 BizTalk 主控件特有規則。 依照預設，所有的閾值監控規則會停用：  
  
- 您的環境，您應該使用特定的臨界值設定一般規則。  
  
- 您應該建立 BizTalk 主控件特有規則為基礎的範本規則和適當的臨界值。  
  
## <a name="monitoring-biztalk-host-instances"></a>監視 BizTalk 主控件執行個體  
 以特定的 BizTalk 主控件為目標的規則會從監視的觀點來看更有彈性。 BizTalk Server 管理組件中提供的 biztalkserverapplication 主控件的閾值監控規則都是範本規則。 若要使用這些規則，您應該使用 Operations Manager 系統管理員主控台：  
  
- 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 規則群組中建立範本規則的複本，然後將它重新命名。  
  
- 建立新的 Operations Manager 提供者的 BizTalk 主控件特有的效能計數器執行個體。  
  
- 修改規則所用的 Operations Manager 提供者，並指向新的。  
  
  假設您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝有 BizTalk 主控件 ReceiveHost，而且您想要監視為此主控件的主控件佇列大小。 在此情況下，您應該建立以 BizTalk 主控件佇列大小的效能計數器的 ReceiveHost 執行個體為基礎的 Operations Manager 提供者。 您也應該針對您的環境適當調整規則中的閾值。  
  
  如果您使用的主控件特有的閾值監控規則，您應該停用一般監控規則。 這可以避免多餘的警示。  
  
## <a name="see-also"></a>另請參閱  
 [使用 System Center Operations Manager 2007 監視 BizTalk Server](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)