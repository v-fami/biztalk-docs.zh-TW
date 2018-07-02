---
title: 步驟 5 （內部）： 產生將訊息插入至 SalesOrder 資料表的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab0bc1a7-8bcd-4110-88e6-4eddf0b57068
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afdca03f5ad8639705ac40171e4142a12c07d757
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973471"
---
# <a name="step-5-on-premises-generate-the-schema-for-inserting-a-message-inito-salesorder-table"></a>步驟 5 （內部）： 產生將訊息插入至 SalesOrder 資料表的結構描述
根據商務案例，從 Contoso 傳送銷售訂單訊息的 X12 必須插入 Northwind **SalesOrder**資料表如果訂購數量大於 100。 若要將訊息插入**SalesOrder**資料表中，您必須產生的結構描述**插入**資料表上的作業。 在本主題中，您將建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案，然後再使用[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]產生的結構描述執行**插入**作業**SalesOrder**資料表。  

### <a name="to-generate-the-schema-for-insert-operation-on-salesorder-table"></a>若要產生 SalesOrder 資料表的插入作業的結構描述  

1. 建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Visual Studio 專案。 從 Visual Studio**檔案**功能表上，按一下**新增**，然後按一下**專案**。 在**新的專案**從清單中已安裝的範本 對話方塊中，按一下**BizTalk 專案**，然後選取**空白[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案**。 針對專案名稱輸入`OrderProcessingDemo`，然後按一下  **確定**。  

2. 以滑鼠右鍵按一下方案總管 中的專案名稱，指向**新增**，然後按一下**新增產生的項目**。  

3. 在 **新增產生的項目**對話方塊中，選取**取用配接器服務**，然後按一下 **新增**。 [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]隨即開啟。  

4. 從**選取的繫結**下拉式清單中，選取**sqlBinding**，然後按一下**設定**。  

5. 在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單，請執行下列其中一項：  


   |  按一下此選項  |                                                                                                                                                               以進行此動作                                                                                                                                                               |
   |--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   **無**   |                                                                                                                                          連接到 SQL Server 使用 Windows 驗證。                                                                                                                                           |
   | **視窗**  |                                                                                                                                          連接到 SQL Server 使用 Windows 驗證。                                                                                                                                           |
   | **使用者名稱** | 指定的使用者名稱和密碼來連接到 SQL Server，藉由指定 SQL Server 資料庫中定義的使用者認證。 請注意，使用者名稱和密碼會區分大小寫。 **注意：** 如果您離開**使用者名稱**並**密碼**空白欄位，配接器連接至使用 Windows 驗證的 SQL Server。 |


6. 按一下  **URI 屬性**索引標籤，然後指定 連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，請參閱 < [SQL Server 連接 URI](http://msdn.microsoft.com/library/dd788089.aspx)。  

   > [!NOTE]
   >  如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  
   > 
   > [!NOTE]
   >  如果您在 [URI 屬性] 索引標籤中未指定任何值[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]將做為 URI `mssql://.//`。 在這種情況下，配接器會連接到預設的資料庫和本機電腦上的預設資料庫執行個體。  

7. 在 [**設定介面卡**] 對話方塊中，按一下**確定**。 在 [**取用配接器服務**] 對話方塊中，按一下**Connect**。  

8. 從**選取一個類別**方塊中，展開**資料表**，然後按一下**SalesOrder**資料表。  

9. 從**可用的類別和作業**方塊中，選取**插入**，按一下**新增**，然後按一下**確定**。 新的項目會新增至 [方案總管] 中。 結構描述檔案 (**TableOperation.dbo.SalesOrder.xsd**) 上執行插入作業產生的結構描述**SalesOrder**資料表。  

## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)