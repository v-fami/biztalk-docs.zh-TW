---
title: "JD Edwards EnterpriseOne 傳輸屬性對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: JDE
helpviewer_keywords: Transport Properties dialog box [JD Edwards EnterpriseOne adapters
ms.assetid: 6a37eeb2-af91-4f58-9699-7a7cbe296862
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21bbb6b4469399aa1952d0a9bdcc41ff7e14c842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="jd-edwards-enterpriseone-transport-properties-dialog-box"></a>JD Edwards EnterpriseOne 傳輸屬性對話方塊
使用 [JD Edwards EnterpriseOne 傳輸屬性] 對話方塊設定配接器必要屬性。  
  
|使用|動作|  
|--------------|----------------|  
|**配接器必要屬性**||  
|Host|輸入主控件伺服器電腦的名稱 (例如， `actsvr1`)。<br /><br /> -或-<br /><br /> 輸入電腦的 IP 位址 (例如， `123.456.0.789`)。|  
|JAVA_HOME|輸入 JDK 安裝的完整路徑 (例如，<br /><br /> `C:\jdk1sdk1.4.2_07`).|  
|JDEdwards 環境|在 JD Edwards EnterpriseOne 中輸入環境的名稱 (例如， `DV7333`)。<br /><br /> DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。|  
|JDEdwards JAR 檔案|輸入每個 JAR 檔案的完整路徑與檔案名稱：<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br /><br /> 每個 JAR 檔案都必須以分號 (;) 分隔，且不得包含空格 (例如，<br /><br /> `<c:>\Connector.jar;<c:>\Kernel.jar;`).|  
|密碼|輸入使用者密碼。 如果您這樣做 useSingle 登入 (SSO)，您必須設定 BizTalk Adapter for JD Edwards EnterpriseOne 來存取伺服器系統的認證參數。 密碼對應至使用者名稱。 密碼決定您存取資料庫時獲得的權限。|  
|通訊埠|輸入的數字識別碼的傳送或接收埠 (例如， `6009`)。|  
|使用者名稱|輸入使用者名稱，然後按一下**確定**。|  
|**啟動程序的資料來源必要的屬性**||  
|資料來源名稱|輸入資料來源的名稱。 此名稱對所有資料類型而言是必要的。|  
|資料庫擁有者|輸入資料庫擁有者的名稱。|  
|資料庫伺服器名稱|輸入資料庫伺服器的名稱。|  
|資料庫伺服器連接埠|輸入識別資料庫伺服器連接埠的數字。|  
|資料庫類型|輸入單一字元以代表資料庫類型。 例如：<br /><br /> **我**-iSeries<br /><br /> **O** -Oracle<br /><br /> **S** -SQL Server<br /><br /> **L** -SQL Server OLEDB<br /><br /> **W** -UDB|  
|實體資料庫名稱|輸入實體資料庫名稱。 所有資料類型都需要有此名稱。|  
|**並行控制**||  
|同時呼叫數目上限|輸入的數值**同時呼叫數目上限**。 這個數字代表同時呼叫數目上限，例如**10**。<br /><br /> 此欄位的預設值是 5。|  
|**重新整理代理程式**||  
|重新整理代理程式|選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。<br /><br /> 例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。|  
|**安全性伺服器**||  
|安全性伺服器名稱|輸入安全性伺服器的名稱。 此欄位是選用的，且預設為 JD Edwards 伺服器主機。|  
|服務名稱連接|輸入安全性伺服器和物件組態對應 (OCM) 使用的連接埠號碼。 預設值為 JD Edwards 伺服器連接埠。|  
|**單一登入**||  
|分支機構應用程式|只有在您使用單一登入 (SSO) 時，才需從下拉式清單中選取分支機構應用程式。|  
|使用 SSO|選取**是**如果您使用 SSO; 密碼就不需要在此情況下。|  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on1.md)   
 [建立分支機構應用程式](../core/creating-affiliate-applications4.md)   
 [BizTalk Adapter for JD Edwards EnterpriseOne 的 UI 參考](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md)