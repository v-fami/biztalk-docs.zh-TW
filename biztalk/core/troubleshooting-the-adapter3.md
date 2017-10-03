---
title: "疑難排解 Adapter3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards OneWorld adapters], connecting [Oracle databases]
- JD Edwards OneWorld adapters, troubleshooting
- troubleshooting [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], troubleshooting
- Oracle databases, connecting [JD Edwards OneWorld adapters]
ms.assetid: 2dd6a951-f113-4f43-b43f-057a239d05c4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15197bcdc84e813d31a8d5292f5559aca1f8ae01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a>配接器疑難排解
此主題中所含的資訊可幫助您識別和解決在使用 Microsoft BizTalk Adapter for JD Edwards OneWorld 時可能會遇到的問題。  
  
## <a name="cannot-use-wildcards-in-send-and-receive-port-properties"></a>傳送與接收埠屬性中無法使用萬用字元  
 Adapter for JD Edwards One World 不支援在下列屬性欄位中使用萬用字元：  
  
|傳送埠屬性|接收埠屬性|  
|------------------------|---------------------------|  
|使用者名稱|事件檔案路徑|  
|JDE 環境|事件目標名稱前置詞|  
|Host||  
|通訊埠||  
|Java_Home||  
|JDE JAR 檔案||  
  
## <a name="connecting-to-oracle-database"></a>連線到 Oracle 資料庫  
 搭配 JD Edwards 使用 Oracle 資料庫時，您必須修改 jdeinterop.ini 檔案。 使用單一登入，[JDBj-ORACLE] 區段會定義 Oracle tnsnames 位置；必須使用資料庫參數；且 SQLNET.ORA 檔案必須存在 BizTalk Server 電腦上 (這應該會隨附在 Oracle Client 中)。  
  
 將下列項目加入至 jdeinterop.ini 檔案：  
  
1.  在 [JDBj-ORACLE] 下，輸入：  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  在 [JDBj-BOOTSTRAP DATA SOURCE] 下，輸入：  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [如何建立 JD Edwards OneWorld 傳送埠](../core/how-to-create-send-ports-for-jd-edwards-oneworld.md)   
 [疑難排解 JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)