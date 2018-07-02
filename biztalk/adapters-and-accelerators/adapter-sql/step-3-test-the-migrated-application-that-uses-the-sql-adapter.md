---
title: 步驟 3： 測試移轉應用程式使用 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 929ce2f3-94ed-4e12-b629-e229769f825a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c2487c6bdf05ae926b8bb962ed9dae6c770298e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973287"
---
# <a name="step-3-test-the-migrated-application-that-uses-the-sql-adapter"></a>步驟 3： 測試移轉應用程式使用 SQL 配接器
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您將測試已移轉的應用程式執行插入作業在 Customer 資料表上的。 若要這樣做，請卸除使用 vPrev 所產生的結構描述的要求訊息[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
  
- 將 BizTalk 協調流程中的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠，以設定 BizTalk 應用程式。  
  
- 設定要用於 Wcf-custom 傳送埠以 WCF 為基礎的 BizTalk 應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1. 建立要求符合 vPrev 所產生的結構描述的 XML [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 使用輸出對應，WCF 自訂傳送連接埠將此選項以 WCF 為基礎的結構描述符合[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]並將它傳送到 SQL Server 資料庫。  
  
   ```  
   <Insert xmlns="http://SQLInsert">  
     <sync>  
       <after>  
         <CustomerTable Name="John" />  
       </after>  
     </sync>  
   </Insert>  
   ```  
  
2. 貼上要對應至檔案的資料夾的要求訊息的接收位置。  
  
3. 協調流程會使用要求訊息，並將它傳送到 SQL Server 資料庫。 在接收到回應從 SQL Server 資料庫結構描述中的 WCF 基礎結構描述符合[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 使用輸入的對應，WCF 自訂傳送連接埠將此結構描述以取得 vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 從 SQL Server 資料庫的回應會儲存到其他的協調流程中定義的檔案位置。 上述的要求訊息的回應是：  
  
   ```  
   <?xml version="1.0" encoding="utf-8" ?>   
   <InsertResponse xmlns="http://SQLInsert">  
     <Success>  
       <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">101</long>   
     </Success>  
   </InsertResponse>  
   ```  
  
    在上述的回應中，"101"會是 Customer 資料表中插入的 identity 資料行的值。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)