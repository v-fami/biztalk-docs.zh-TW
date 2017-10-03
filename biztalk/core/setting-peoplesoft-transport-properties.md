---
title: "設定 PeopleSoft 傳輸屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: 44b5f015-59f1-43a3-9673-a5ba40266843
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ecfd221d28312e84dcbaf7d8c83abc4f5191f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-peoplesoft-transport-properties"></a>設定 PeopleSoft 傳輸屬性
PeopleSoft 傳輸屬性用於設計和執行階段。 在**傳輸屬性**對話方塊中，您設定的連接和認證參數特定伺服器系統和您嘗試存取的物件。  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  展開 [配接器必要屬性]，並填入連線至 PeopleSoft 伺服器的所有必要資訊。  
  
     您必須設定組態參數，Microsoft BizTalk Adapter for PeopleSoft Enterprise 才能連線至 PeopleSoft Enterprise。 此資料區分大小寫。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |`Application Server Path`|字串，表示執行 PeopleSoft Application Server 的電腦和接聽的連接埠。 PeopleSoft 8 應用程式的 URL 路徑的語法是 / / < 電腦名稱 >:\<連接埠 >。 詢問您的 PeopleSoft 系統管理員以\<連接埠 > 值。 \<連接埠 > 值是 JOLT 通訊協定接聽程式通訊埠，不應用程式伺服器連接埠。 預設 JOLT 連接埠為 9000。|  
    |`JAVA_HOME`|設定 JAVA_HOME 變數以指向 JDK 安裝，例如： **C:\j2sdk1.4.2_08**。|  
    |`Password`|如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。<br /><br /> 字串，表示使用者用來登入 PeopleSoft 系統的密碼。 字元不會顯示出來，而是以星號 (*) 表示。|  
    |`PeopleSoft 8.x Jar Files`|若要使用 Ccmponent 介面 (僅限 PeopleSoft 8)，您必須更新 CLASSPATH 來包含 PeopleSoft 元件介面 jar 檔案。 例如： **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**。|  
    |`User Name`|如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。<br /><br /> 字串，表示登入 PeopleSoft 系統所需的使用者名稱。|  
  
2.  輸入**其他參數**時使用日期做為索引鍵的值; 它有不同的格式。 YYYY-MM-DD 是預設格式。  
  
3.  輸入**並行控制**值中代表的呼叫，例如 200，**同時呼叫數目上限**如有必要。  
  
     **同時呼叫數目上限**參數啟動的多載保護，如果後端伺服器無法處理的資料量。 同時呼叫是指配接器尚未回覆的要求。 設定**同時呼叫數目上限**在輸送量超過後端處理能力。  
  
     此欄位 的預設值為 -1，表示不會提供保護 。  
  
     如果 BizTalk Server 提交要求至傳輸配接器的並行連線數目呼叫等於或超過設定的值**同時呼叫數目上限**、 送出要求會儲存，直到同時呼叫數目的執行緒若要減少設定值以下。  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft 傳送處理常式](../core/creating-peoplesoft-send-handlers.md)