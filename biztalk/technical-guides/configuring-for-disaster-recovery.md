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
ms.openlocfilehash: 3899b27324fa00e0b5c630c7be4433f65a917a1b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-for-disaster-recovery"></a>設定災害復原
BizTalk Server 記錄傳送功能延伸現有的備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業。 BizTalk Server 記錄傳送就不需要手動還原一系列的備份作業所產生的備份組，並在系統失敗時減少停機時間。 BizTalk Server 記錄傳送是 BizTalk 嚴重損壞修復程序的重要元件。  
  
> [!NOTE]  
>  每個應用程式的小組必須有記錄的備份和還原補充本主題提供的概念的災害復原計畫。 整體計劃應可解決整個系統，包括應用程式和作業系統的元件。  
  
 執行嚴重損壞修復作業是非常類似於以手動方式執行的 BizTalk 群組，一組新的還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體。 主要差異是該 BizTalk Server 記錄檔傳送適用於持續在災害復原站台，儲存許多手動步驟的記錄檔。 因此，記錄檔的上一組必須以手動方式還原當 BizTalk Server 實作記錄傳送。 否則，後面的所有記錄備份，最後一個完整備份之後的最後一個完整備份必須以手動方式還原。 BizTalk Server 記錄傳送會減少此手動程序，加速災害復原站台的還原作業所需的時間。  
  
 本節涵蓋有關 production 組態來加速災害復原程序的建議事項。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備災害復原站台](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [記錄傳送的使用者帳戶和角色](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a>請參閱  
 [災害復原](../technical-guides/disaster-recovery.md)