---
title: 連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93e56c1f-adee-4976-bc39-bb9b8102145e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12c815fbfe2b723a0dd4e4646fd7b69a7e30b01f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215062"
---
# <a name="connect-to-the-oracle-database-in-visual-studio-using-the-add-adapter-service-reference"></a>連接到 Oracle 資料庫，在 Visual Studio 中使用配接器加入服務參考
若要連接到 Oracle 資料庫使用[!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="connect-using-the-add-adapter-service-reference-plug-in"></a>使用加入的配接器服務參考外掛程式連接  
完成下列步驟來連接 Oracle 資料庫使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。   

  
1.  若要使用連接[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]程式設計方案中：  
  
    1.  建立使用 Visual Studio 專案。  
  
    2.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。 此時會開啟 新增配接器服務參考外掛程式。  
  
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
 [連接到 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)   
 [連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)