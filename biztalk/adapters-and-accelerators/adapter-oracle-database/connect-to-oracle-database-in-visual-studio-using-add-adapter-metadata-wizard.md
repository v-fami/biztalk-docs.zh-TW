---
title: 連接到 Visual Studio 中使用 新增配接器中繼資料精靈中的 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 726b3f82-887c-407a-bb9f-dcb9443155b0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fe5ebb085055307730f65cd36fea29f68deeccf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996535"
---
# <a name="connect-to-oracle-database-in-visual-studio-using-add-adapter-metadata-wizard"></a>連接到 Oracle 資料庫，在 Visual Studio 中使用 新增配接器中繼資料精靈
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也會公開為 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述您想要使用配接器的 Oracle 資料庫上執行的作業。  

 本主題說明如何使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

## <a name="connecting-to-an-oracle-database-using-the-add-adapter-metadata-wizard"></a>連接到 Oracle 資料庫使用新增配接器中繼資料精靈  
 執行下列步驟來連接 Oracle 資料庫使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-connect-to-an-oracle-database"></a>若要連接到 Oracle 資料庫  

1. 若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：  

   1. 以滑鼠右鍵按一下方案總管 中的專案，指向**新增**，然後按一下**新增產生的項目**。  

   2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


      |    使用    |           以進行此動作            |
      |----------------|---------------------------------|
      | **類別** |     按一下 **新增介面卡**。      |
      | **範本**  | 按一下 **新增配接器中繼資料**。 |


   3. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

   4. 在 [新增配接器中繼資料精靈] 中，選取**Wcf-oracledb**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  

      > [!IMPORTANT]
      >  如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。  

   5. 按 [下一步] 。  

2. 從**選取的繫結**下拉式清單中，選取**oracleDBBinding**然後按一下**設定**。  

3. 中**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫。  

   1. 若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。 請確定指定使用者名稱和密碼以連接到 Oracle 資料庫時，您遵守下列考量：  

      - **使用者名稱**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留開啟的 Oracle 資料庫上的連接時，您輸入使用者名稱值的大小寫。 Oracle 資料庫上的使用者名稱會區分大小寫。 您應該確定您提供 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。 一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫:"SCOTT"。  

      - **密碼**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會保留在開啟的 Oracle 資料庫上的連接時，您輸入密碼的值的大小寫。 如需版本 10g 及更早版本，則 Oracle 系統上的密碼並不區分大小寫。  

   2. 若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。  

4. 按一下  **URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  

5. 按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 例如，如果您想要以 POLLINGSTMT 作業為目標，您必須設定**PollingStatement**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。

   > [!NOTE]
   >  如果您要產生使用新增的配接器中繼資料精靈 的中繼資料，而且您選取現有的 Wcf-oracledb 傳送埠時，您需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

6. 按一下 [確定] 。  

7. 按一下 **[連接]**。 建立連線之後，連線狀態會顯示為**Connected**。  

    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。  

    ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")  

## <a name="see-also"></a>另請參閱  
 [連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md)   
 [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)