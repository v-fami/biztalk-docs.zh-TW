---
title: JD Edwards OneWorld 傳輸屬性對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- JDEOneWorld
helpviewer_keywords:
- Transport Properties dialog box [JD Edwards OneWorld adapters]
ms.assetid: 34d6b5d0-4bd9-4522-a540-8415d3143762
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 625479ef124aad6d7c0b10cde34b45a142ff9f90
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015895"
---
# <a name="jd-edwards-oneworld-transport-properties-dialog-box"></a>JD Edwards OneWorld 傳輸屬性對話方塊
使用 [JD Edwards OneWorld 傳輸屬性] 對話方塊設定配接器必要屬性。  
  
|使用|動作|  
|--------------|----------------|  
|**配接器必要屬性**||  
|Host|輸入主控件伺服器電腦的名稱 (例如， `actsvr1`)。<br /><br /> -或-<br /><br /> 輸入電腦的 IP 位址 (例如， `123.456.0.789`)。|  
|JAVA_HOME|輸入 JDK 安裝的完整路徑。|  
|JDEdwards 環境|在 JD Edwards OneWorld 中輸入環境的名稱 (例如， `DV7333`)。<br /><br /> DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。|  
|JDEdwards JAR 檔案|輸入每個 JAR 檔案的完整路徑與檔案名稱：<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br />-BTSLIBInterop.jar<br /><br /> 必須以分號 （;），且不得包含空格分隔每個 jar 檔案 (例如， `<c:>\Connector.jar;<c:>\Kernel.jar;`)。|  
|密碼|輸入使用者密碼。 如果不使用單一登入 (SSO)，您必須為 BizTalk Adapter for JDEdwards OneWorld 設定認證參數以存取伺服器系統。 密碼對應至使用者名稱。 密碼決定您存取資料庫時獲得的權限。|  
|通訊埠|輸入的數字識別碼的傳送或接收埠 (例如， `6009`)。|  
|使用者名稱|輸入使用者名稱，然後按一下**確定**。|  
|同時呼叫數目上限|輸入的數值**同時呼叫數目上限**。 這個數字代表同時呼叫數目上限，例如**10**。<br /><br /> 此欄位的預設值是**5**，表示未啟用保護，就會發生。|  
|重新整理代理程式|選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。<br /><br /> 例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。|  
|分支機構應用程式|只有在您使用 SSO 時才需從清單中選取分支機構應用程式。|  
|使用 SSO|選取**是**如果您使用 SSO; 密碼就不需要在此情況下。|  
  
## <a name="see-also"></a>另請參閱  
 [在配接器的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [建立分支機構應用程式](../core/creating-affiliate-applications3.md)   
 [BizTalk Adapter for JDE OneWorld 的 UI 參考](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md)