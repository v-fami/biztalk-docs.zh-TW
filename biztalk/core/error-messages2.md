---
title: "錯誤 Messages2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages, JD Edwards OneWorld adapters
- adapters [JD Edwards OneWorld adapters], error messages
- JD Edwards OneWorld adapters, error messages
ms.assetid: 9fb65d50-83c6-426e-a0d6-674800ecf70f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84b26891592162c553fb270d2d8c9482f1c2b4d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-messages"></a>錯誤訊息
下表說明 JD Edwards OneWorld 系統中的錯誤訊息，並提供可能的更正方式。  
  
|錯誤識別碼|可能的原因 / 錯誤描述|可能的更正方式|  
|--------------|-----------------------------------------|-------------------------|  
|**E JDE0002**|遺失 JD Edwards OneWorld JAR 檔案。<br /><br /> 無法為 JD Edwards OneWorld Java Data Bean 產生類別物件。|確認儲存機制的路徑。<br /><br /> 如需詳細資訊，請參閱[基本型別](../core/basic-types1.md)。|  
|**E JDE0027**|遺失 JD Edwards OneWorld JAR 檔案。 無法取得 JD Edwards OneWorld 連線物件。|確認您的 CLASSPATH 環境變數。<br /><br /> 請參閱「更新 CLASSPATH」。<br /><br /> 確認您的認證。<br /><br /> 如需詳細資訊，請參閱[基本型別](../core/basic-types1.md)。|  
||遺失 JD Edwards OneWorld JAR 檔案。<br /><br /> 儲存機制的路徑錯誤。|確認 jdeinterop.ini 的位置。 確認 jdeinterop.ini 檔中設定的儲存機制的路徑。<br /><br /> 將 JD Edwards OneWorld 商務程序匯入其他電腦時，您必須手動複製 jdeinterop.ini。|  
||無法取得 JD Edwards OneWorld 連線物件。|確認您的 CLASSPATH 設定和登入認證。|  
|**我-JDE0043**|錯誤的應用程式伺服器、連接埠、環境、組態檔路徑、使用者、密碼。<br /><br /> 登入失敗。|確認您的登入認證。<br /><br /> 如需詳細資訊，請參閱[基本型別](../core/basic-types1.md)。|  
|**我-JDE0048**|如果 jdearglist.txt 檔案不存在或內容空白，記錄檔中就會在 Microsoft BizTalk Adapter for JD Edwards OneWorld 開啟時出現一則資訊訊息。|更新 jdearglist.txt 檔案以輸入參數的清單，使參數自動靠右對齊並在左側填滿空格。<br /><br /> 請參閱[處理字串值](../core/handling-string-values1.md)。<br /><br /> 您每次變更 jdearglist，就必須重新產生該商務物件的結構描述。|  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 資料類型](../core/appendix-a-data-types.md)   
 [疑難排解 JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)