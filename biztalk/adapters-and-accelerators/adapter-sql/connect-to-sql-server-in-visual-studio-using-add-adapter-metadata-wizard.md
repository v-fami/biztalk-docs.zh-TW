---
title: 連接到 SQL Server 在 Visual Studio 使用新增配接器中繼資料精靈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2169722d-beba-4d96-a54b-54986ece9bf8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6de95e2e6906a840e0e41d013f6c1e1e0a73a8d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981399"
---
# <a name="connect-to-sql-server-in-visual-studio-using-add-adapter-metadata-wizard"></a>連接到 SQL Server 在 Visual Studio 使用新增配接器中繼資料精靈
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]也會公開為 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述您想要使用配接器的 SQL Server 上執行的作業。  

## <a name="connecting-to-sql-server-using-add-adapter-metadata-wizard"></a>連接到 SQL Server 使用新增配接器中繼資料精靈  
 執行下列步驟來連接 SQL Server 使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-connect-to-sql-server"></a>若要連接到 SQL Server  

1. 若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：  

   1. 建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

   2. 以滑鼠右鍵按一下方案總管 中的專案名稱，指向**新增**，然後按一下**新增產生的項目**。  

   3. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


      |    使用    |           以進行此動作            |
      |----------------|---------------------------------|
      | **類別** |     按一下 **新增介面卡**。      |
      | **範本**  | 按一下 **新增配接器中繼資料**。 |


   4. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

   5. 在 [新增配接器精靈] 中，選取**WCF-SQL**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  

      > [!IMPORTANT]
      >  如果您已經設定在 BizTalk WCF SQL 連接埠，請選取 從連接埠**連接埠**清單。  

   6. 按 [下一步] 。  

2. 從**選取的繫結**下拉式清單中，選取**sqlBinding**，然後按一下**設定**。  

3. 在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單，請執行下列其中一項：  

   > [!NOTE]
   >  如果您要連接到 SQL Server 使用 Windows 驗證，Windows 您登入，必須將的使用者加入至 SQL Server 中所述[連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  

   |  按一下此選項  |                                                                                                                                                               以進行此動作                                                                                                                                                               |
   |--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   **無**   |                                                                                                                                         使用 Windows 驗證連接到 SQL Server。                                                                                                                                         |
   | **視窗**  |                                                                                                                                         使用 Windows 驗證連接到 SQL Server。                                                                                                                                         |
   | **使用者名稱** | 指定的使用者名稱和密碼來連接到 SQL Server，藉由指定 SQL Server 資料庫中定義的使用者認證。 請注意，使用者名稱和密碼會區分大小寫。 **注意：** 如果您離開**使用者名稱**並**密碼**空白欄位，配接器連接至使用 Windows 驗證的 SQL Server。 |


4. 按一下  **URI 屬性**索引標籤，然後指定 連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  

   > [!NOTE]
   >  如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  
   > 
   > [!NOTE]
   >  如果您在 [URI 屬性] 索引標籤中未指定任何值[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]將做為 URI `mssql://.//`。 在這種情況下，配接器會連接到預設的資料庫和本機電腦上的預設資料庫執行個體。  

5. 按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 如需有關繫結屬性，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  

   > [!NOTE]
   >  如果您要產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]並且選取現有的 WCF SQL 傳送埠，您不需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

6. 按一下 [確定] 。  

7. 按一下 **[連接]**。 建立連線之後，連線狀態會顯示為**Connected**。  

    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。 圖形化使用者介面是相同的[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

    ![連接到 SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")  

    [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點，其中包含可以在 SQL Server 執行的各種作業。 例如，**程序**節點包含所有可供您連接之資料庫的程序。 同樣地，**資料表**節點包含您連接的資料庫，以及可以在資料表執行的作業中的所有資料表。 如需有關這些節點的詳細資訊，請參閱 <<c0> [ 中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md)。  

## <a name="see-also"></a>另請參閱  
 [連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)