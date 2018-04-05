---
title: 錯誤 Messages1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error messages
ms.assetid: db9c9634-3f4b-4b38-b3ba-388e587fccd8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80a44049c43c499ac05a8a6f296d11add934267a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-messages"></a>錯誤訊息
下表說明 JD Edwards EnterpriseOne 系統中的錯誤訊息並提供可能的更正方式。  
  
|錯誤識別碼|可能的原因 / 錯誤描述|可能的更正方式|  
|--------------|-----------------------------------------|-------------------------|  
|E-JDE0027|遺失 JD Edwards EnterpriseOne JAR 檔案。 無法取得 JD Edwards EnterpriseOne 連線物件。|確認您的認證。 確認您的 CLASSPATH 設定和登入認證。 請參閱環境變數。|  
|I-JDE0043|錯誤的應用程式伺服器、連接埠、環境、組態檔路徑、使用者、密碼。 登入失敗。|確認您的登入認證。 請參閱環境變數。|  
|I-JDE0048|如果 jdearglist.txt 檔案不存在或內容空白，記錄檔中就會在 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 開啟時出現一則資訊訊息。|更新 jdearglist.txt 檔案以輸入參數的清單，使參數自動靠右對齊並在左側填滿空格。 如需詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。 您每次變更 jdearglist，就必須重新產生該商務物件的結構描述。|  
|E-JDE0027|無法取得 JD Edwards EnterpriseOne 連線物件。 請檢查您的 CLASSPATH 和認證。|確認 jdeinterop.ini 位置。|  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)   
 [技術參考](../core/technical-reference6.md)