---
title: "連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting, to the Oracle database
- connection, to the Oracle database
ms.assetid: db2789d0-2d61-472b-ad0c-4ef0707e9c64
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9ecd6867776b8adf918f901369f526bc0479bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service"></a>連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務
使用配接器服務增益集安裝時安裝 WCF LOB 配接器 SDK。 使用配接器服務在載入增益集安裝在電腦上的所有 WCF 自訂繫結。 若要連接到使用 WCF 型 Oracle 資料庫[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 BizTalk 專案中，您必須使用**oracleDBBinding**。  
  
 本主題說明如何使用配接器服務增益集使用。  
  
## <a name="connecting-to-an-oracle-database-using-the-consume-adapter-service-add-in"></a>連接到 Oracle 資料庫使用配接器服務增益集  
 執行下列步驟來連接 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
1.  若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：  
  
    1.  以滑鼠右鍵按一下方案總管] 中的專案，指向**新增**，然後按一下 [**新增產生的項目**。  
  
    2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
        |使用|動作|  
        |--------------|----------------|  
        |**類別**|按一下**取用配接器服務**。|  
        |**範本**|按一下**取用配接器服務**。|  
  
    3.  按一下 **[加入]**。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]隨即開啟。  
  
2.  從**選取繫結**下拉式清單中選取**oracleDBBinding**按一下**設定**。  
  
3.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連接到 Oracle 資料庫。  
  
    1.  若要使用的 Oracle 資料庫的認證連接，資料庫中輸入認證**使用者名**和**密碼**文字方塊。 請確定您遵守下列項目指定的使用者名稱和密碼以連接到 Oracle 資料庫時：  
  
        -   **使用者名稱**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的使用者名稱值的大小寫。 Oracle 資料庫上的使用者名稱會區分大小寫。 您應該確定您提供的 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。 一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫才:"SCOTT"。  
  
        -   **密碼**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的密碼值的大小寫。 如需版本 10g 和更早版本，則 Oracle 系統上的密碼並不區分大小寫。  
  
    2.  若要使用 Windows 驗證進行連接，輸入 **/** 中**使用者名**文字方塊並保留**密碼**文字方塊留白。  
  
4.  按一下**URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
5.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 例如，如果您想要以 POLLINGSTMT 作業為目標，您必須設定**PollingStatement**繫結屬性。 如需繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
6.  按一下 **[確定]**。  
  
7.  按一下 **[連接]**。 建立連接之後，連線狀態會顯示為**Connected**。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。  
  
     ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")  
  
## <a name="see-also"></a>另請參閱  
 [連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md)   
 [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)