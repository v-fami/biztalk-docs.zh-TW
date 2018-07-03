---
title: 使用 Operations Manager 2007 監視的最佳作法 |Microsoft Docs
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
ms.openlocfilehash: d099ba9ea60fd8f553d4eaf2011e93a054f59e68
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018698"
---
# <a name="best-practices-for-monitoring-with-operations-manager-2007"></a>使用 Operations Manager 2007 監視的最佳做法
遵循本主題，有效地監視您的應用程式使用 Operations Manager 2007 中列出的最佳作法。  
  
 **安裝其他管理組件，如需更完整的涵蓋範圍**  
  
- 為了協助確保 Operations Manager 2007 監視重要的應用程式，在您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，您應該安裝下列管理組件：  
  
  - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] （必要）  
  
  - Windows Server 作業系統 （選擇性）  
  
  - Microsoft Windows Server 容錯移轉叢集 （如果叢集使用的選擇性）  
  
  - SQL Server 監視  
  
  - Internet Information Services 7  
  
  - 訊息佇列 (MSMQ) 5.0 （選擇性）  
  
  **檢閱並設定每日警示優先順序**  
  
- 每日檢視警示並排定其優先順序有助於確保適時解決問題。  
  
  **確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與 Operations Manager 2007 伺服器進行通訊。**  
  
- 如果執行的伺服器間的通訊失敗[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]及監視基礎結構中，您將不會收到警示。  
  
  **啟用和停用規則視**  
  
- 依照預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理封包中的部分規則會停用。 這些已停用的規則屬於下列類型： 需要自訂、 做為範本的規則和規則，以便監視其他規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]事件。 請確定相關規則程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境會啟用。  
  
  **自訂規則，視您的環境**  
  
- 您應該自訂中的規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，以符合您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。 某些規則需要監視的閾值或時間精心定義的臨界值會根據您的特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。  
  
  **建立額外的規則，必要時，根據規則中包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件**  
  
- 規則可做為您建立成品，例如範本提供使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機。 建立下列成品專用規則時，您應該使用這些範本規則做為參考：  
  
  -   主應用程式特定的規則，例如，裝載佇列監控 」，而裝載節流監視  
  
  -   MessageBox 專用規則  
  
  -   其他協力廠商元件的規則，例如 MQSeries 配接器  
  
  **監視所有 BizTalk Server 相關元件**  
  
  組成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]確定它們都在執行時，您應監視的環境包括但不是一定是限制為：  
  
- BizTalk 主控件執行個體  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 使用安裝的代理程式作業 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- 開發 BizTalk 解決方案的任何自訂服務  
  
- 開發 BizTalk 解決方案的任何自訂資料庫的狀態  
  
- 任何自訂事件記錄檔項目與相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境  
  
## <a name="see-also"></a>另請參閱  
 [使用 System Center Operations Manager 2007 監視 BizTalk Server](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)