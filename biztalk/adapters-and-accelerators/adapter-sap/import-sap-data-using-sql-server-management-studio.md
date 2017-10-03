---
title: "使用 SQL Server Management Studio 的 SAP 資料匯入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- SQL Server Management Studio, importing data
ms.assetid: c8151c6d-4b33-40fe-9b83-9bed27df9a99
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28981d2130e82a094e470de1e2b6904382be56b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="import-sap-data-using-sql-server-management-studio"></a>使用 SQL Server Management Studio 匯入 SAP 資料
本節提供有關如何使用 SQL Server Management Studio 從 SAP 系統的資料匯入到 SQL Server 資料庫的資訊。 本節提供有關如何建立 SSIS 封裝，您可以執行匯入資料的指示。 本章節也會提供有關如何執行 SSIS 封裝的資訊。  
  
## <a name="prerequisites"></a>必要條件  
 然後再執行本主題提供的程序，請確定：  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]已安裝在電腦上。  
  
-   在電腦上安裝 SQL Server Business Intelligence Development Studio。  
  
### <a name="to-import-data-using-sql-server-management-studio"></a>若要使用 SQL Server Management Studio 匯入資料  
  
1.  啟動 SQL Server Management Studio。  
  
2.  在**連接到伺服器**對話方塊方塊中，指定要連接到 SQL Server 資料庫，然後按一下值**連接**。 **Microsoft SQL Server Management Studio**隨即開啟。  
  
3.  在**物件總管] 中**、 依序展開 [SQL Server 名稱、 展開**資料庫**，以滑鼠右鍵按一下資料庫，其中您將會匯出資料表從 SAP 系統。 從內容功能表，指向**工作**，然後按一下**匯入資料**。 這會啟動**SQL Server 匯入和匯出精靈**。  
  
4.  閱讀歡迎] 畫面中，然後按一下上的資訊**下一步**。  
  
5.  在**選擇資料來源**對話方塊中，從**資料來源**下拉式選單**.NET Framework Data Provider for mySAP Business Suite**。 對話方塊會列出不同的連線參數，以連接至 SAP 系統。 一般連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要：  
  
    -   輸入連接的連接參數。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援連線類型 A、 B 和 d。若要連接到 SAP 系統必須提供連接參數的任何*一個*一種連線類型。 比方說，連接類型的您必須提供應用程式伺服器主機和系統編號的名稱。  
  
    -   若要連接到 SAP 系統，例如使用者名稱和密碼登入資訊。  
  
     如需有關連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[了解 Data Provider for SAP 連接字串](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
     在**選擇資料來源**對話方塊方塊中，指定：  
  
    -   連接類型之參數的任何一個連線。  
  
    -   要連接至 SAP 系統的登入資訊。  
  
    -   您是否要啟用 SAP GUI 偵錯。  
  
    -   您是否要使用 RFC SDK 追蹤。  
  
     按一下 **[下一步]**。  
  
6.  在**選擇目的地**對話方塊：  
  
    1.  從**目的地**下拉式清單中，選取**SQL Native Client**。  
  
    2.  從**伺服器名稱**下拉式清單中，選取 [SQL server 名稱。  
  
    3.  選取驗證模式。  
  
    4.  從**資料庫**下拉式清單中，選取您要匯入 SAP 資料表的資料庫。  
  
    5.  按一下 **[下一步]**。  
  
7.  在**指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項，然後按一下**下一步**。  
  
8.  在**提供來源查詢**對話方塊方塊中，指定 SELECT 查詢來篩選要匯入 SQL Server 的資料。 如需文法的 SELECT 查詢[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[語法選取陳述式 SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。  
  
     按一下**剖析**按鈕驗證查詢，並按一下**確定**快顯對話方塊方塊中。 按一下 **[下一步]**。  
  
9. 在**選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。 來源是您指定要從 SAP 擷取資料的查詢。 目的地是將 SQL Server 資料庫中建立的資料表。  
  
10. 精靈會建立預設的對應來源與目的地之間資料表欄位。 不過，您可以變更對應，根據您的需求。 若要變更欄位對應，請按一下**編輯對應**。  
  
     ![SAP 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")  
  
11. 在**資料行對應**對話方塊中，您可以：  
  
    -   變更目的地資料表中的資料行的名稱。  
  
    -   忽略特定資料行與目的地資料表中。  
  
    -   變更目的地資料表中的欄位的資料類型。  
  
    -   變更其他欄位屬性，例如可為 null，大小、 精確度和小數位數。  
  
    -   按一下 **[確定]**。  
  
12. 在**選取來源資料表和檢視**對話方塊中，按一下 [**下一步**。  
  
13. 在**儲存並執行封裝**對話方塊中，  
  
    -   選取**立即執行**核取方塊，以執行查詢。  
  
    -   選取**儲存 SSIS 封裝**核取方塊，來將查詢儲存為封裝和更新版本執行。 如果您選擇儲存封裝，您也必須指定您是否要將封裝儲存在 SQL Server 或檔案系統。  
  
    -   從**封裝保護等級**下拉式清單中，選取封裝層級的保護，然後指定認證必要。  
  
    -   按一下 **[下一步]**。  
  
     如果您選擇儲存封裝，請繼續進行下一個步驟。 否則，請跳至步驟 15。  
  
14. 在**儲存 SSIS 封裝**對話方塊方塊中，指定：  
  
    -   封裝名稱  
  
    -   套件描述  
  
    -   如果您選擇將封裝儲存至 SQL server，請選取 [從 SQL Server**伺服器名稱**下拉式清單。  
  
    -   如果您選擇將封裝儲存至檔案系統中，指定的名稱和位置中的檔案**檔案名稱**文字方塊。  
  
    -   按一下 **[下一步]**。  
  
15. 在**完成精靈**對話方塊方塊中，檢閱精靈將執行，並按一下動作的摘要**完成**。  
  
16. 在**執行運算**對話方塊中，精靈會啟動執行工作，以從 SAP 的資訊匯入到 SQL Server 資料庫資料表。 每個工作的狀態會顯示在精靈中。  
  
17. 所有工作都執行成功之後，請按一下**關閉**。 如果工作失敗，請參閱對應的錯誤訊息、 修正問題，和重新執行精靈。  
  
## <a name="running-the-ssis-package"></a>執行 SSIS 封裝  
 如果您選擇儲存 SSIS 封裝，您可以執行它從 SAP 系統中擷取最新的資訊。 本節提供如何執行封裝，如果您選擇將它儲存到檔案系統資訊。  
  
#### <a name="to-run-the-package-from-windows-explorer"></a>若要從 Windows 檔案總管中執行封裝  
  
1.  從**Windows 檔案總管**、 瀏覽至您儲存封裝的位置，然後按兩下封裝。  
  
2.  在**執行封裝公用程式**對話方塊中，按一下 [ **Execute**。  
  
3.  **封裝執行進度**對話方塊會顯示不同的工作的進度。  
  
4.  所有工作都執行成功之後，請按一下**關閉**。  
  
5.  在**執行封裝公用程式**對話方塊中，按一下 [**關閉**。  
  
 如需有關執行封裝的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972)。 任何其他相關資訊的 SSIS 封裝，請參閱[http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973)。  
  
## <a name="verifying-the-results"></a>驗證結果  
 執行封裝之後, 您必須確認結果，請前往 SAP 資料匯入的 SQL Server 資料庫。 執行封裝應該目的地資料庫中建立資料表並填入從 SAP 資料表的值。  
  
## <a name="see-also"></a>另請參閱  
 [適用於 SAP 使用 SSIS 中使用資料提供者](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)