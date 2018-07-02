---
title: 合作對象解析管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ad728ff-4d7c-4ab3-af0e-76006576dce5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20a466c2de29859b6a971fd34540d6a806da9fe1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977079"
---
# <a name="party-resolution-pipeline-component"></a>合作對象解析管線元件

## <a name="overview"></a>概觀
合作對象解析管線元件的責任是對應傳送者憑證或傳送者安全性識別碼 (SID) 至所對應已設定的 BizTalk Server 合作對象。  

 當合作對象解析元件讀取內送訊息時，它會兩個訊息內容屬性作為輸入： **WindowsUser**並**SignatureCertificate**。 **WindowsUser**屬性會填入配接器，或自訂管線元件，它可以可靠地衍生傳送者資訊的傳送者的使用者名稱使用。 **SignatureCertificate**會填入配接器或 MIME/SMIME 解碼器管線元件，用戶端驗證憑證的指紋。  

 若訊息已簽章，則用以驗證輸入訊息簽章的憑證指紋就會用以查詢「組態儲存機制」，以決定它與哪些合作對象相關聯。 若找到合作對象，就會將該合作對象的 SourcePartyID 放置在訊息內容中以作為訊息的建立者。  

 若要啟用合作對象解析管線元件以驗證 Windows 使用者，您必須將 "WindowsUser" 別名新增至合作對象。 在 名稱 和 辨識符號的欄位中輸入"WindowsUser"，並將值設定為 使用者名稱格式為\<網域 \ 使用者名稱\>(e.g.SOMEDOMAIN\someuser)。 在獨立的實例中，用以設定合作對象的 WindowsUser 值應符合接收配接器所設定的值。  

 如果在訊息到達兩個屬性加上戳記的合作對象解析元件，合作對象解析元件會先嘗試依憑證解析合作對象 (假設**依憑證解析合作對象**屬性設定為 **，則為 True**)。 如果合作對象解析，該合作對象的 SourcePartyID 放置在訊息的內容中以作為訊息的 OriginatorPID 如果執行管線的主控件程序標示為**信任的驗證**的管線。 若不能使用憑證完成合作對象解析，則在訊息上的 OriginatorPID 值會加上 "s-1-5-7" 的戳記，此為匿名使用者的 SID。 如需 OriginatorPID 屬性的詳細資訊，請參閱[如何保護管線](../core/how-to-secure-pipelines.md)。  

## <a name="resolve-the-party"></a>解析合作對象  
 下表顯示合作對象解析管線元件嘗試解析合作對象的方式。  

|依 SID|依憑證|WindowsUser|SignatureCertificate|結果|  
|------------|--------------------|-----------------|--------------------------|------------|  
|True|False|可用|可用或無法使用|合作對象已解析。|  
|True|False|無法使用|可用或無法使用|合作對象未解析並加上匿名的戳記。|  
|False|True|可用或無法使用|可用或無法使用|合作對象未解析並加上匿名的戳記。|  
|True|True|可用|可用|合作對象已解析。|  
|True|True|無法使用|可用或無法使用|合作對象未解析並加上匿名的戳記。|  
|False|False|可用或無法使用|可用或無法使用|合作對象未解析並加上匿名的戳記。|  

 如需設定 「 合作對象解析 」 管線元件的資訊，請參閱[如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md)。  

## <a name="see-also"></a>另請參閱  
- **訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [管線元件](../core/pipeline-components.md)   
- [自訂合作對象解析 (BizTalk Server 範例)](../core/custom-party-resolution-biztalk-server-sample.md)   
- [程序之間的訊息驗證](../core/authentication-of-messages-between-processes.md)
