---
title: 若要建立報表伺服器專案中使用適用於 SAP 的資料提供者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fe985b5-ba67-4179-a31c-4f41106c32be
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f57155b386af979f1da52d39d062aff171203b5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008199"
---
# <a name="use-the-data-provider-for-sap-to-create-a-report-server-project"></a>若要建立報表伺服器專案中使用適用於 SAP 的資料提供者
您必須建立報表伺服器專案，使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，以產生報告的可用 SAP 系統中的資料。 本主題提供有關如何建立報表伺服器專案的指示。  
  
## <a name="prerequisites"></a>必要條件  
 然後再執行本主題所提供的程序，請確定您安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]安裝時[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]一部分[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝。 如需詳細資訊[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，請參閱安裝指南位於\<*安裝磁碟機*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
### <a name="to-create-a-report-server-project"></a>若要建立報表伺服器專案  
  
1. 啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並建立報表伺服器專案。 若要建立報表伺服器專案，執行下列作業：  
  
   1.  按一下 **檔案**功能表上，按一下**新增**，然後按一下**專案**。  
  
   2.  在 [**新的專案**] 對話方塊中，從**專案類型**清單中，選取**商業智慧專案**。 從**Visual Studio 安裝的範本**清單中，選取**報表伺服器專案**。  
  
   3.  指定的名稱和專案的位置，然後按一下**確定**。 本主題中，指定做為專案名稱`SAP_ Report`。  
  
2. 加入新的資料來源：  
  
   1. 從 [方案總管] 中，以滑鼠右鍵按一下**共用資料來源**，然後按一下**加入新的資料來源**。  
  
   2. 在 **共用資料來源**對話方塊中，於**一般**索引標籤上，指定資料來源的名稱。 本主題中，將名稱指定為`SAPDataSource`。  
  
   3. 從**型別**清單中，選取**Data Provider for SAP**。  
  
   4. 在 **連接字串**方塊中，指定的連接字串[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。 如需[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連接字串，請參閱 <<c2> [ 閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
       ![建立資料來源](../../adapters-and-accelerators/adapter-sap/media/8494c1a5-5e68-4178-a005-a6ea56d97ad7.gif "8494c1a5-5e68-4178-a005-a6ea56d97ad7")  
  
      > [!NOTE]
      >  您可以選擇隨連接字串中指定的認證，或指定它們下, 一個步驟中所述。  
  
   5. 在 **認證**索引標籤上，選擇下列項目，其中，然後按一下**確定**:  
  
      |使用|以進行此動作|  
      |--------------|----------------|  
      |**使用特定的使用者名稱和密碼**|指定使用者名稱和密碼來連線到 SAP 系統。|  
      |**提示輸入認證**|在產生報告時，SAP 系統的輸入的認證。 **注意：** 認證您指定這個選項會覆寫的認證，如果指定，為連接字串的一部分。|  
      |**無認證**|如果您要為連接字串的一部分提供的使用者名稱和密碼，請選擇這個選項。|  
  
      > [!NOTE]
      >  Windows 驗證模式不支援報表伺服器專案。  
  
3. 加入新的報表：  
  
   1. 從 [方案總管] 中，以滑鼠右鍵按一下**報表**，然後按一下**加入新的報表**。  
  
       這會啟動 「 報表精靈 」。  
  
   2. 閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。  
  
   3. 在 **選取資料來源**對話方塊方塊中，選擇**共用資料來源**選項，然後選取**SAPDataSource**您在上一個步驟中，建立，然後按一下  **下一步**。  
  
   4. 如果您選擇**提示認證**選項來建立資料來源時指定的使用者認證**輸入資料來源認證** 對話方塊隨即出現。 指定使用者名稱和密碼以連接到 SAP 系統，然後按一下**確定**。  
  
       如果您選擇任何其他選項來指定認證，此精靈會繼續下一個步驟。  
  
   5. 在 **設計查詢**對話方塊方塊中，指定用來產生報表的查詢字串。 例如：  
  
      ```  
      SELECT TOP 2 KUNNR, NAME1 FROM KNA1 WHERE NAME1 LIKE @PARAM  
      ```  
  
       此查詢會擷取前兩筆記錄，從 KNA1 NAME1 所在的資料表產生報告時，您將指定的名稱。  
  
       按 [下一步] 。  
  
   6. 在後續的對話方塊中，您可以設計想要顯示報表的格式。 如果您想要使用的預設格式，請按一下**完成 >>&#124;**  ，直接移至**完成**對話方塊。  
  
   7. 在 [**完成精靈**] 對話方塊中，指定報表的名稱，檢閱 [摘要]，然後按一下**完成**。 本主題中，指定做為報表名稱`SAPReport`。  
  
      您現在可以檢視報表。 如需有關如何檢視報表的指示，請參閱 <<c0> [ 檢視的報表，適用於 SAP](../../adapters-and-accelerators/adapter-sap/view-the-reports-for-sap.md)。  
  
## <a name="see-also"></a>另請參閱  
 [搭配使用 Data Provider for SAP 與 SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)