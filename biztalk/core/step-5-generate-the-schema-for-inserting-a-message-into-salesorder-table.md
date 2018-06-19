---
title: 步驟 5 （內部部署）： 產生插入訊息插入至 SalesOrder 資料表的結構描述 |Microsoft 文件
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
ms.openlocfilehash: facb5d638ed82e1632e434a2a9c9063a2c3daa68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279318"
---
# <a name="step-5-on-premises-generate-the-schema-for-inserting-a-message-inito-salesorder-table"></a>步驟 5 （內部部署）： 產生插入訊息插入至 SalesOrder 資料表的結構描述
根據商務案例，從 Contoso 傳送銷售訂單訊息的 X12 必須插入至 Northwind 的**SalesOrder**資料表如果訂購數量大於 100。 若要將訊息插入**SalesOrder**資料表中，您必須產生的結構描述**插入**資料表上的作業。 在本主題中，您將建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案，然後使用[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]產生結構描述執行**插入**作業**SalesOrder**資料表。  
  
### <a name="to-generate-the-schema-for-insert-operation-on-salesorder-table"></a>若要產生 SalesOrder 資料表的 Insert 作業的結構描述  
  
1.  建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Visual Studio 專案。 從 Visual Studio**檔案**功能表上，按一下 **新增**，然後按一下 **專案**。 在**新專案**對話方塊中，從已安裝的範本清單中按一下**BizTalk 專案**，然後選取**空[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案**。 針對專案名稱輸入`OrderProcessingDemo`，然後按一下 **確定**。  
  
2.  以滑鼠右鍵按一下方案總管] 中的專案名稱，指向**新增**，然後按一下 [**新增產生的項目**。  
  
3.  在**新增產生的項目**對話方塊中，選取**取用配接器服務**，然後按一下 **新增**。 [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]隨即開啟。  
  
4.  從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**。  
  
5.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單中，執行下列其中一項：  
  
    |按一下此選項|動作|  
    |----------------|----------------|  
    |**無**|連接到 SQL Server 使用 Windows 驗證。|  
    |**視窗**|連接到 SQL Server 使用 Windows 驗證。|  
    |**使用者名稱**|指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。 請注意使用者名稱和密碼會區分大小寫。 **注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。|  
  
6.  按一下**URI 屬性**索引標籤，然後再指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，請參閱[SQL Server 連接 URI](http://msdn.microsoft.com/library/dd788089.aspx)。  
  
    > [!NOTE]
    >  如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
    > [!NOTE]
    >  如果您在 [URI 屬性] 索引標籤中未指定任何值[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]將做為 URI `mssql://.//`。 在這種情況下，配接器連接到預設的資料庫和本機電腦上的預設資料庫執行個體。  
  
7.  在**設定配接器**對話方塊中，按一下 **確定**。 在**取用配接器服務**對話方塊中，按一下 **連接**。  
  
8.  從**選取類別目錄**方塊中，展開 **資料表**，然後按一下  **SalesOrder**資料表。  
  
9. 從**可用的類別和作業**方塊中，選取**插入**，按一下 **新增**，然後按一下 **確定**。 新的項目會加入至 [方案總管] 中。 結構描述檔案 (**TableOperation.dbo.SalesOrder.xsd**) 是產生的結構描述上執行插入作業的**SalesOrder**資料表。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)