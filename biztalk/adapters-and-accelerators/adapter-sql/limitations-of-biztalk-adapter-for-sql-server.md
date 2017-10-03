---
title: "限制 BizTalk adapter for SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a19b109-a6b7-452f-a544-48627fa52f36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a80990a9e3f417b64a06d8823300d53b2c4f3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-sql-server"></a>BizTalk adapter for SQL Server 的限制
下列已知限制[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:  
  
-   [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援 SQL Server 資料庫中建立同義字。 SQL Server 中的同義字的相關資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=120111](http://go.microsoft.com/fwlink/?LinkId=120111)。  
  
-   如果您變更執行的電腦的系統時間[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機，時間不會自動更新中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機。 這可能會導致不正確的行為，使用的接收埠的輸入作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 因應措施，您必須重新啟動後已變更其執行之電腦的系統時間有接收埠的主控件執行個體。  
  
-   如果預存程序中的參數名稱包含 127 或多個字元，則無法執行預存程序使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 這是因為 ADO.NET 的限制。  
  
-   WSDL[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]產生，轉換為 proxy 時，會公開為 System.DateTime DateTimeOffset 資料行。 此資料類型無法儲存時區資訊。 因此，配接器傳送到 proxy 的任何日期/時間值會轉換成.NET 應用程式中的本機時間。 如果您想要保留的時區資訊，您必須變更您的 proxy 使用 String 型別，而不是 System.DateTime 的介面。 然後，使用 XmlConvert.ToDateTimeOffset 建立 Sytstem.DateTimeOffset 物件，它可以儲存時區資訊。  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)