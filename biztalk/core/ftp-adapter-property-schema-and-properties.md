---
title: FTP 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [FTP adapters], schemas
- FTP adapters, properties
- BeforePut property [FTP adapters]
- PassiveMode property [FTP adapters]
- configuring [FTP adapters], properties
- UserName property, FTP adapters
- SSOAffiliateApplication property [FTP adapters]
- AfterPut property [FTP adapters]
- ReceivedFileName property [FTP adapters]
- RepresentationType property [FTP adapters]
- SpoolingFolder property [FTP adapters]
- FTP adapters, schemas
- CommandLogFileName property [FTP adapters]
- AllocateStorage property [FTP adapters]
- schemas, FTP adapters
- Password property [FTP adapters]
- MaxConnections property [FTP adapters]
ms.assetid: 677fdb61-c2b0-4df2-a826-840113e61e8b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cf72847fccd84a1435e436a4bf2b59d36e26179
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006135"
---
# <a name="ftp-adapter-property-schema-and-properties"></a>FTP 配接器屬性結構描述和屬性
下表包含 FTP 配接器屬性結構描述中的屬性。  
  
 **命名空間：** http://schemas.microsoft.com/BizTalk/2003/ftp-properties  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**RepresentationType**|xs:string|指定 FTP 配接器如何傳送資料。<br /><br /> **有效值：** 二進位或 ASCII|  
|**SSOAffiliateApplication**|xs:string|指定要用於 FTP 傳送埠的「企業單一登入」分支機構應用程式。|  
|**UserName**|xs:string|指定傳送訊息時，用來登入 FTP 伺服器的使用者名稱。|  
|**密碼**|xs:string|指定傳送訊息時，用來登入 FTP 伺服器的密碼。|  
|**BeforePut**|xs:string|指定檔案 PUT 之前要執行的 FTP 命令，例如要在 FTP 伺服器上變更預設值的命令。 使用分號 (;) 來分隔命令。 不需要開啟命令。|  
|**AfterPut**|xs:string|指定檔案 PUT 後要執行的 FTP 命令。 使用分號 (;) 來分隔命令。|  
|**ReceivedFileName**|xs:string|指定 FTP 配接器從中讀取訊息之檔案的完整名稱。|  
|**MaxConnections**|xs:unsignedInt|指定伺服器最多可以開啟的並行 FTP 連線數目。 值為 0 時表示沒有限制。|  
|**CommandLogFileName**|xs:string|指定要儲存一份可用來診斷錯誤條件時傳送或接收透過 FTP 檔案的記錄檔的位置。|  
|**AllocateStorage**|xs:boolean|此選項已被取代，在 BizTalk Server 中，不建議使用這個屬性。|  
|**PassiveMode**|xs:boolean|指定配接器與 FTP 伺服器之間的連接模式。<br /><br /> 在主動模式下，FTP 伺服器會連線到 FTP 配接器所開啟的連接埠。 在被動模式下，FTP 配接器會連線到 FTP 伺服器所開啟的連接埠。<br /><br /> 如果**PassiveMode**是 false，則配接器連接到 FTP 伺服器使用主動模式。 此屬性的預設值是 false。|  
|**SpoolingFolder**|xs:string|指定 FTP 伺服器上的暫存資料夾位置。 使用此選項可確保從傳輸失敗復原。|  
|**UseSsl**|xs:boolean|指定 FTP 配接器是否需使用 SSL 以和 FTPS 伺服器通訊。|  
|**UseDataProtection**|xs:boolean|指定是否針對檔案傳輸使用 SSL 加密。 如果配接器傳送或接收來自 FTPS 伺服器的資料檔時必須使用 SSL 加密，請選擇 True。 若選擇 False，配接器會以純文字格式傳送和接收資料檔。|  
|**FtpsConnectionMode**|xs:string|指定與 FTP 伺服器建立的 SSL 連線模式。<br /><br /> **有效值：** 隱含或明確|  
|**ClientCertificateHash**|xs:string|指定必須用於安全通訊端層 (SSL) 交涉的用戶端憑證 SHA1 雜湊。<br /><br /> 系統會根據此雜湊，從用於執行 BizTalk 主控件執行個體之使用者帳戶的個人存放區挑選用戶端憑證。|  
  
## <a name="see-also"></a>請參閱  
 [設定 FTP 配接器](../core/configuring-the-ftp-adapter.md)
 
 [FTP 配接器的最佳做法和建議](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)
 
 [FTP 配接器](../core/ftp-adapter.md)