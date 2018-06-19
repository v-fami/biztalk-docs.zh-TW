---
title: 使用 Operations Manager 2007 監視的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a5026c-ef59-498b-9bef-ea0f1c932eae
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29d83f647c40801260890a99cef4b0b2bfa0551b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300222"
---
# <a name="best-practices-for-monitoring-with-operations-manager-2007"></a>使用 Operations Manager 2007 監視的最佳作法
遵循本主題，有效地監視應用程式使用 Operations Manager 2007 中列出的最佳作法。  
  
 **安裝更完整的涵蓋範圍的其他管理組件**  
  
-   若要協助確保 Operations Manager 2007 監視的主要應用程式中您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，您應該安裝下列管理組件：  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（必要）  
  
    -   Windows Server 作業系統 （選擇性）  
  
    -   Microsoft Windows Server 容錯移轉叢集 （如果叢集使用的選擇性）  
  
    -   SQL Server 監視  
  
    -   Internet Information Services 7  
  
    -   訊息佇列 (MSMQ) 5.0 （選擇性）  
  
 **檢閱並設定每日警示優先順序**  
  
-   每日檢視警示並排定其優先順序有助於確保適時解決問題。  
  
 **確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與 Operations Manager 2007 伺服器進行通訊。**  
  
-   如果執行的伺服器之間的通訊失敗[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與監視基礎結構，您將不會收到警示。  
  
 **啟用和停用規則視**  
  
-   依照預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理封包中的部分規則會停用。 這些停用的規則屬於下列類型： 需要自訂、 做為範本、 規則和規則，以便監視其他規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]事件。 請確定相關規則程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境會啟用。  
  
 **自訂規則，視您的環境**  
  
-   您應該自訂中的規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，以符合您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。 某些規則需要根據您的特定監視閾值或時間閾值精心定義[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。  
  
 **建立額外的規則，在必要時，根據規則中包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件**  
  
-   規則可提供做為您建立成品，例如範本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機。 建立下列成品專用規則時，您應該使用這些範本規則做為參考：  
  
    -   主控件專用規則，例如裝載佇列監控 」，並裝載節流監視  
  
    -   MessageBox 專用規則  
  
    -   其他協力廠商元件的規則，例如 MQSeries 配接器  
  
 **監視所有 BizTalk Server 相關元件**  
  
 元件的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以確保它們執行，您應監視包括但不是一定限於：  
  
-   BizTalk 主控件執行個體  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]安裝的代理程式作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   開發 BizTalk 解決方案的任何自訂服務  
  
-   開發 BizTalk 解決方案的任何自訂資料庫的狀態  
  
-   適用於任何自訂事件記錄檔項目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境  
  
## <a name="see-also"></a>另請參閱  
 [監控 BizTalk Server 與 System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)