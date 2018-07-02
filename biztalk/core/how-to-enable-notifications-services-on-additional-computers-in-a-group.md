---
title: 如何在群組中的其他電腦上啟用 Notifications Services |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 571d6b45-b0cc-47f2-bed3-7c6f3e70decc
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fd8a1a49be2416fb8b7fe5d160dd5228a95e94f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983391"
---
# <a name="how-to-enable-notifications-services-on-additional-computers-in-a-group"></a>如何在群組中的其他電腦啟用 Notification Services
當執行 BAM 時在多重電腦環境中，您必須啟用 Notification Services，您將會用來執行 BAM 管理公用程式來部署活動的每一部電腦上。  
  
 請考慮下列案例：  
  
- 群組 A 包含下列電腦：  
  
  - 電腦 1 當做 BAM 管理電腦。  
  
  - 電腦 2 裝載 BAM PIT 和「星狀結構描述」資料庫。  
  
  - 電腦 3 裝載 BAM「封存」和「分析」資料庫。  
  
  - 電腦 4 裝載 BAM「警示」資料庫。  
  
  - 電腦 5 裝載其餘的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫。  
  
- 群組 B：  
  
  -   電腦 6 當做 BAM 管理電腦，其所有資料庫與群組 A 共用。  
  
  若要從群組 B 的電腦將活動部署至群組 A 的資料庫，您必須在裝載告知服務的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 註冊 Notification Services。 如果未註冊 Notification Service，您將會收到下列錯誤訊息：  
  
  正在部署警示...錯誤： BAM 部署失敗。  
  
  未部署警示。  
  
  引動過程的目標傳回例外狀況。  
  
  找不到指定的 Notification Services 執行個體的登錄項目。  
  
### <a name="to-register-notifications-services-additional-computers"></a>在其他電腦中註冊 Notification Services  
  
1.  在電腦上的其他群組中，按一下**開始**，指向**所有程式**，按一下  **Microsoft SQL Server 2005**，按一下 **組態工具**，然後按一下**Notification Services 命令提示字元**。  
  
2.  在命令提示字元中，輸入： **nscontrol register-名稱\<NS 前置詞的名稱，在設定選擇\>-伺服器\<ns db 的 sql server\>**。 這樣可以讓 Notification Services 登入正確的資料庫 (這項資訊是在服務電腦的登錄中由 nscontrol 執行維護)。  
  
## <a name="see-also"></a>另請參閱  
 [變更 BAM 執行階段設定](../core/changing-bam-runtime-settings.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)