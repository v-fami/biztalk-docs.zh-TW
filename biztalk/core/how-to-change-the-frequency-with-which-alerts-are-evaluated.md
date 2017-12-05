---
title: "如何變更警示的頻率會評估 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68f326ed-2017-4853-89b9-146cb0785554
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f921699e9a98724c8ca2c36f99d7eb9b9848875
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-change-the-frequency-with-which-alerts-are-evaluated"></a>如何變更評估警示的頻率
以預設設定部署時，有時候 SQL Notification Services 產生器可能無法跟上 BAM 事件提供者引發事件的速度。 您可以修改 Notification Services 的 adf.xml 檔案，針對警示增加評估事件的頻率 (配量持續時間)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以具有「主要匯入」資料庫讀寫權限的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組 (通常是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的「系統管理員」群組) 成員登入。  
  
### <a name="to-modify-the-notification-services-generator-quantum-duration"></a>若要修改 Notification Services 產生器配量持續時間  
  
1.  開啟 [Notification Services 命令提示字元]。 按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2005**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。  
  
2.  取得 Notification Services 的組態檔。 在命令提示字元中，輸入： **cscript ProcessBamNSFiles.vbs-Get config.xml adf.xml \<PimaryImport 資料庫伺服器\> \< PimaryImport 資料庫名稱\>**。  
  
3.  修改或加入\<QuantumDuration\>項目底下\<u\>節點在 adf.xml 檔案中。 如需 QuantumDuration 項目的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803)。  
  
4.  在命令提示字元中，輸入： **cscript ProcessBamNSFiles.vbs-更新 config.xml adf.xml \<PimaryImport 資料庫伺服器\> \< PimaryImport 資料庫名稱\>。**  
  
## <a name="see-also"></a>請參閱  
 [Notification Services 設定檔的 BAM 命令列指令碼](../core/bam-command-line-script-for-notification-services-configuration-files.md)