---
title: "SQL 配接器中設定動態連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98b66ed-0bf7-4b24-9d16-9792d033b818
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bb1417280706399728f7bfd59bc4c5ee7a7cc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dynamic-ports-in-the-sql-adapter"></a>SQL 配接器中設定動態連接埠
在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。 因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 架構的配接器，您可以動態設定的連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用訊息內容屬性。  

## <a name="use-an-expression-shape"></a>使用 「 運算式 」 圖形  
 如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後以指定**運算式**圖形，如下列範例所示：  
  
```  
Request2=Request1;  
Request2(WCF.Action)="TableOp/Insert/dbo/CustomerTable";  
Request2(WCF.BindingType)="sqlBinding";  
Request2(WCF.UserName)="myuser";  
Request2(WCF.Password)="mypass";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="mssql://sql_server/my_instance/my_database";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  如果您使用 WCF SQL 配接器在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SQLAdapter"`，其中**SQLAdapter**新增 WCF-SQL 配接器中的名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 在上述範例中，  
  
-   正在從 Request1 訊息建立 Request2 訊息。 這兩個訊息對應至作業結構描述，產生使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
-   傳送埠是 BizTalk 協調流程中的邏輯傳送埠的名稱。  
  
 **運算式**圖形是 BizTalk 協調流程的一部分。 部署協調流程也會建立一個 WCF 自訂傳送連接埠。  
  
 如需設定動態連接埠的詳細資訊，請參閱[設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)