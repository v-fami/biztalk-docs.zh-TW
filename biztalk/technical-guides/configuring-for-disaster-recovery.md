---
title: "設定災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acdafe68-c8bf-4064-afca-6dfd22d15052
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c6a188255097f0a1c1e85086688252f9154b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-for-disaster-recovery"></a>設定災害復原
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送功能可延伸現有的備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送就不需要手動還原一系列的備份作業所產生的備份組，以及在系統失敗時減少停機時間。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送是 BizTalk 嚴重損壞修復程序的重要元件。  
  
> [!NOTE]  
>  每個應用程式的小組必須有記錄的備份和還原補充本主題提供的概念的災害復原計畫。 整體計劃應可解決整個系統，包括應用程式和作業系統的元件。  
  
 執行嚴重損壞修復作業是非常類似於以手動方式執行的 BizTalk 群組，一組新的還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體。 主要的差別在於[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送會套用記錄檔，持續災害復原站台，儲存許多手動步驟。 因此，記錄檔的上一組必須以手動方式還原當[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]實作記錄傳送。 否則，後面的所有記錄備份，最後一個完整備份之後的最後一個完整備份必須以手動方式還原。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送會減少此手動程序，加速災害復原站台的還原作業所需的時間。  
  
 本節涵蓋有關 production 組態來加速災害復原程序的建議事項。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備災害復原站台](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [記錄傳送的使用者帳戶和角色](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a>另請參閱  
 [嚴重損壞修復](../technical-guides/disaster-recovery.md)