---
title: BizTalk Adapter for SQL Server 的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a19b109-a6b7-452f-a544-48627fa52f36
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195701e4bba469a7faaab36a5ae1636c5abca5f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967383"
---
# <a name="limitations-of-biztalk-adapter-for-sql-server"></a>BizTalk Adapter for SQL Server 的限制
下列已知限制[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:  
  
- [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援在 SQL Server 資料庫中建立的同義字。 SQL Server 中的同義字的相關資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=120111 ](http://go.microsoft.com/fwlink/?LinkId=120111)。  
  
- 如果您變更執行的電腦的系統時間[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機，時間不會自動更新在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主應用程式。 這可能會導致不正確的行為，使用的接收埠的輸入作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 因應措施，您必須重新啟動主控件執行個體，您已變更執行它的電腦的系統時間之後的接收埠。  
  
- 如果預存程序中的參數名稱不可超過 127 個以上的字元，您無法執行預存程序使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 這是因為 ADO.NET 的限制。  
  
- WSDL[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]產生時，轉換為 proxy 時，會公開為 System.DateTime 的 DateTimeOffset 資料行。 此資料類型無法儲存時區資訊。 如此一來，配接器傳送至 proxy 的任何日期/時間值會轉換成.NET 應用程式中的當地時間。 如果您想要保留的時區資訊，您必須變更您的 proxy，而不是 System.DateTime 使用字串類型的介面。 然後，使用 XmlConvert.ToDateTimeOffset 建立 Sytstem.DateTimeOffset 物件，它可以儲存時區資訊。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)