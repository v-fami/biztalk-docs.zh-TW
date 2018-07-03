---
title: 匯入 Siebel 資料使用 SQL Server Management Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio, importing data by using
- how to, import data by using SQL Server Management Studio
ms.assetid: 67da7f7b-37ea-4a31-89ef-a9f6974ff976
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdcc6140bb50ebca299cd58f78063be8f108dea4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013175"
---
# <a name="import-siebel-data-using-sql-server-management-studio"></a>匯入使用 SQL Server Management Studio 的 Siebel 資料
本節提供如何使用 SQL Server Management Studio Siebel 系統的資料匯入到 SQL Server 資料庫的相關資訊。 它也會提供有關如何建立和執行 SSIS 套件，此資料匯入的指示。  
  
## <a name="prerequisites"></a>必要條件  
 然後再執行本主題所提供的程序，請確定：  
  
- [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]安裝在電腦上。  
  
- 在電腦上安裝 SQL Server Business Intelligence Development Studio。  
  
## <a name="importing-data-by-using-sql-server-management-studio"></a>使用 SQL Server Management Studio 匯入資料  
 執行下列步驟將資料匯入從 Siebel 系統使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 SQL Server Management Studio。  
  
#### <a name="to-import-data-by-using-sql-server-management-studio"></a>若要使用 SQL Server Management Studio 匯入資料  
  
1. 啟動 SQL Server Management Studio。  
  
2. 在 **連接到伺服器**對話方塊方塊中，指定的值，以連接到 SQL Server 資料庫，然後按一下**Connect**。 此時會開啟 Microsoft SQL Server Management Studio。  
  
3. 在 物件總管 中，展開 SQL Server 名稱、 依序展開**資料庫**，以滑鼠右鍵按一下資料庫，其中您將會將資料表匯出來自 Siebel 系統。 從操作功能表，指向**任務**，然後按一下**匯入資料**。 這會啟動 SQL Server 匯入和匯出精靈。  
  
4. 閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。  
  
5. 在 [**選擇資料來源**] 對話方塊中，從**資料來源**下拉式清單中，選取 **.NET Framework Data Provider for Siebel eBusiness 應用程式**。 指定不同的連接屬性的值[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]連接字串。 如需連接字串屬性的詳細資訊，請參閱[Siebel 連接字串的資料提供者屬性](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。  
  
    按 [下一步] 。  
  
6. 在 [**選擇目的地**] 對話方塊中：  
  
   1.  從**目的地**下拉式清單中，選取**SQL Native Client**。  
  
   2.  從**伺服器名稱**下拉式清單中，選取 SQL Server 名稱。  
  
   3.  選取驗證模式。  
  
   4.  從**資料庫**下拉式清單中，選取您要匯入 Siebel 的資料表的資料庫。  
  
   5.  按 [下一步] 。  
  
7. 在 **指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項。  
  
8. 在 **提供來源查詢**對話方塊方塊中，指定選取的查詢，以篩選要匯入到 SQL Server 的資料。 如需詳細資訊，選取 「 了解文法查詢[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，請參閱 < [Siebel 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。  
  
    按一下 [**剖析**按鈕以驗證查詢中，按一下 **[確定]** 中的快顯對話方塊中，然後按一下**下一步]**。  
  
9. 在 **選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。 來源是您指定用來擷取 Siebel 的資料的查詢。 目的地是將 SQL Server 資料庫中建立的資料表。  
  
10. 精靈會建立預設的對應來源與目的地之間資料表欄位。 不過，您可以變更對應，根據您的需求。 若要變更欄位對應，請按一下**編輯對應**。  
  
     ![Siebel 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")  
  
11. 在 [**資料行對應**] 對話方塊中，您可以：  
  
    -   變更目的地資料表中的資料行的名稱。  
  
    -   忽略特定的目的地資料表中的資料行。  
  
    -   變更目的地資料表中的欄位資料類型。  
  
    -   變更其他欄位屬性，例如可為 null，大小、 有效位數和小數位數。  
  
         完成後，請按一下 **[確定]**。  
  
12. 在 **選取來源資料表和檢視表** 對話方塊中，按一下**下一步**。  
  
13. 在 [**儲存並執行套件**] 對話方塊中：  
  
    - 選取 **立即執行**核取方塊以執行查詢。  
  
    - 選取 **儲存 SSIS 封裝**核取方塊，將查詢儲存為封裝，並稍後再執行它。 如果您選擇儲存封裝，您也必須指定是否要將封裝儲存在 SQL Server 或檔案系統。  
  
    - 從**套件保護等級**下拉式清單中，選取封裝層級的保護，並指定認證要求。  
  
    - 按 [下一步] 。  
  
      如果您選擇儲存封裝，請繼續下一個步驟。 否則，請跳至步驟 15。  
  
14. 在 **儲存 SSIS 封裝**對話方塊方塊中，指定下列項目：  
  
    -   封裝的名稱  
  
    -   套件描述  
  
    -   如果您選擇將封裝儲存至 SQL Server，請選取 從 SQL Server**伺服器名稱**下拉式清單。  
  
    -   如果您選擇將封裝儲存至檔案系統中，指定的名稱和位置中的檔案**檔案名**文字方塊。  
  
         完成後，請按一下 [下一步]。  
  
15. 在 **完成精靈**對話方塊方塊中，檢閱精靈將會執行，然後再按一下的動作的摘要**完成**。  
  
16. 在 [**正在執行作業**] 對話方塊中，精靈會啟動執行工作，以從 Siebel 將資訊匯入到 SQL Server 資料庫資料表。 每個工作的狀態會顯示在精靈中。  
  
17. 所有工作都成功都執行之後，請按一下**關閉**。 如果工作失敗，請參閱對應的錯誤訊息、 修正問題，並返回精靈。  
  
## <a name="running-the-ssis-package"></a>執行 SSIS 套件  
 如果您選擇儲存 SSIS 封裝，您可以執行它來擷取 Siebel 系統中的最新的資訊。 本節提供如何執行封裝，如果您選擇將它儲存至檔案系統的相關資訊。  
  
#### <a name="to-run-the-package-from-windows-explorer"></a>若要從 Windows 檔案總管中執行封裝  
  
1. 從**Windows 檔案總管**，瀏覽至您儲存封裝的位置，按兩下封裝。  
  
2. 在 **[執行封裝公用程式]** 對話方塊中，按一下 **[執行]**。 **封裝執行進度** 對話方塊中顯示的不同工作的進度。  
  
3. 所有工作都成功都執行之後，請按一下**關閉**。  
  
4. 在 **[執行封裝公用程式]** 對話方塊中，按一下 **[關閉]**。  
  
   執行封裝的詳細資訊，請參閱 < 執行封裝 >，網址[ http://go.microsoft.com/fwlink/?LinkId=94972 ](http://go.microsoft.com/fwlink/?LinkId=94972)。 針對任何其他資訊與 SSIS 封裝，查看 「 封裝使用說明主題 (SSIS) 」 [ http://go.microsoft.com/fwlink/?LinkId=94973 ](http://go.microsoft.com/fwlink/?LinkId=94973)。  
  
## <a name="verifying-the-results"></a>驗證結果  
 執行封裝之後, 您必須移至要匯入 Siebel 資料的 SQL Server 資料庫來驗證結果。 執行封裝應該已建立資料表的目的地資料庫中。 此資料表應該填入 Siebel 資料表中的值。  
  
## <a name="see-also"></a>另請參閱  
 [搭配使用 Data Provider for Siebel 與 SSIS](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)