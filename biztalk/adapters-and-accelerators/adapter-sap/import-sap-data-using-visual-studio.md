---
title: 使用 Visual Studio 的 SAP 資料匯入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- importing SAP data, using Visual Studio
- Visual Studio, importing SAP data
ms.assetid: 70cce089-232d-4ab9-81bd-6b0d6f0097d7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1295f763815872bacedf2262f7c022d6813bd75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217750"
---
# <a name="import-sap-data-using-visual-studio"></a>使用 Visual Studio 的 SAP 資料匯入
本節提供有關如何使用 Microsoft 的資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]SAP 系統的資料匯入至 SQL Server 資料庫。 本節提供有關如何建立 SSIS 封裝，您可以執行匯入資料的指示。 本章節也會提供有關如何執行 SSIS 封裝的資訊。  
  
## <a name="prerequisites"></a>必要條件  
 然後再執行本主題提供的程序，請確定：  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]已安裝在電腦上。  
  
-   [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]已安裝在電腦上。  
  
### <a name="to-import-data-using-visual-studio"></a>若要使用 Visual Studio 匯入資料  
  
1.  啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]建立整合服務專案。  
  
2.  從**專案**功能表上，選取**SSIS 匯入和匯出精靈**。 這會啟動**SQL Server 匯入和匯出精靈**。  
  
3.  閱讀歡迎 畫面中，然後按一下上的資訊**下一步**。  
  
4.  在**選擇資料來源**對話方塊中，從**資料來源**下拉式選單 **.NET Framework Data Provider for mySAP Business Suite**。 對話方塊會列出不同的連線參數，以連接至 SAP 系統。 一般連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要：  
  
    -   輸入連接的連接參數。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援連線類型 A、 B 和 d。若要連接到 SAP 系統必須提供連接參數的任何*一個*一種連線類型。 比方說，連接類型的您必須提供應用程式伺服器主機和系統編號的名稱。  
  
    -   若要連接到 SAP 系統，例如使用者名稱和密碼登入資訊。  
  
     如需有關連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[了解 Data Provider for SAP 連接字串](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
     在**選擇資料來源**對話方塊方塊中，指定：  
  
    -   連接類型之參數的任何一個連線。  
  
    -   要連接至 SAP 系統的登入資訊。  
  
    -   您是否要啟用 SAP GUI 偵錯。  
  
    -   您是否要使用 RFC SDK 追蹤。  
  
     按一下 **[下一步]**。  
  
5.  在**選擇目的地**對話方塊：  
  
    1.  從**目的地**下拉式清單中，選取**SQL Native Client**。  
  
    2.  從**伺服器名稱**下拉式清單中，選取 SQL server 名稱。  
  
    3.  選取驗證模式。  
  
    4.  從**資料庫**下拉式清單中，選取您要匯入 SAP 資料表的資料庫。  
  
    5.  按一下 **[下一步]**。  
  
6.  在**指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項，然後按一下**下一步**。  
  
7.  在**提供來源查詢**對話方塊方塊中，指定 SELECT 查詢來篩選要匯入 SQL Server 的資料。 如需文法的 SELECT 查詢[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。  
  
     按一下**剖析**按鈕驗證查詢，並按一下**確定**快顯對話方塊方塊中。 按一下 **[下一步]**。  
  
8.  在**選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。 來源是您指定要從 SAP 擷取資料的查詢。 目的地是將 SQL Server 資料庫中建立的資料表。  
  
9. 精靈會建立預設的對應來源與目的地之間資料表欄位。 不過，您可以變更對應，根據您的需求。 若要變更欄位對應，請按一下**編輯對應**。  
  
     ![SAP 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")  
  
10. 在**資料行對應**對話方塊中，您可以：  
  
    -   變更目的地資料表中的資料行的名稱。  
  
    -   忽略特定資料行與目的地資料表中。  
  
    -   變更目的地資料表中的欄位的資料類型。  
  
    -   變更其他欄位屬性，例如可為 null，大小、 精確度和小數位數。  
  
    -   按一下 **[確定]**。  
  
11. 在**選取來源資料表和檢視**對話方塊中，按一下 **下一步**。  
  
12. 在**完成精靈**對話方塊方塊中，檢閱精靈將執行，並按一下動作的摘要**完成**。  
  
13. 在**正在執行作業**對話方塊中，精靈會啟動執行工作，以從 SAP 的資訊匯入到 SQL Server 資料庫資料表。 每個工作的狀態會顯示在精靈中。  
  
14. 所有工作都執行成功之後，請按一下**關閉**。 如果工作失敗，請參閱對應的錯誤訊息、 修正問題，和重新執行精靈。  
  
15. 精靈會新增至您的整合服務專案的 SSIS 封裝。 儲存整合服務專案。  
  
## <a name="running-the-ssis-package"></a>執行 SSIS 封裝  
 一旦整合服務專案中建立封裝時，您可以將它從 SAP 系統的資料匯入到 SQL Server 資料庫執行。 執行下列步驟來執行封裝來匯入 SAP 資料。  
  
#### <a name="to-run-the-package-from-visual-studio"></a>若要從 Visual Studio 執行封裝  
  
1.  瀏覽至 [方案總管] 中的 SSIS 封裝。  
  
2.  以滑鼠右鍵按一下封裝名稱，然後選取**執行封裝**。  
  
 如需有關執行封裝的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972)。 任何其他相關資訊的 SSIS 封裝，請參閱[http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973)。  
  
## <a name="verifying-the-results"></a>驗證結果  
 執行封裝之後, 您必須確認登入 SQL Server，並巡覽到 SAP 資料匯入的資料庫的結果。 執行封裝應該目的地資料庫中建立資料表並填入從 SAP 資料表的值。  
  
## <a name="see-also"></a>另請參閱  
 [適用於 SAP 使用 SSIS 中使用資料提供者](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)