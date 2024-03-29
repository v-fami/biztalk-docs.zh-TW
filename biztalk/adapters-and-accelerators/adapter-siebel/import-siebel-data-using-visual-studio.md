---
title: 匯入 Siebel 資料使用 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33701361-eca2-4795-a5e0-78162a98e9ba
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d631c461c876ef4066e497d7d72d2e5fe13d022
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978031"
---
# <a name="import-siebel-data-using-visual-studio"></a>使用 Visual Studio 的 Siebel 資料匯入
本節提供有關如何使用 Microsoft 的資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Siebel 系統的資料匯入到 SQL Server 資料庫。 它也會提供有關如何建立和執行 SSIS 套件，此資料匯入的指示。  
  
## <a name="prerequisites"></a>必要條件  
 然後再執行本主題所提供的程序，請確定：  
  
- [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]安裝在電腦上。  
  
- Microsoft Visual Studio 會安裝在電腦上。  
  
## <a name="import-in-visual-studio"></a>在 Visual Studio 中的匯入  
 
1. 啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並建立的整合服務專案。  
  
2. 從**專案**功能表上，選取**SSIS 匯入和匯出精靈**。 這會啟動 SQL Server 匯入和匯出精靈。  
  
3. 閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。  
  
4. 在 [**選擇資料來源**] 對話方塊中，從**資料來源**下拉式清單 **.NET Framework Data Provider for Siebel eBusiness 應用程式**。 指定不同的連接屬性的值[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]連接字串。 如需連接字串屬性的詳細資訊，請參閱[Siebel 連接字串的資料提供者屬性](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。  
  
    按 [下一步] 。  
  
5. 在 [**選擇目的地**] 對話方塊中：  
  
   1.  從**目的地**下拉式清單中，選取**SQL Native Client**。  
  
   2.  從**伺服器名稱**下拉式清單中，選取 SQL Server 名稱。  
  
   3.  選取驗證模式。  
  
   4.  從**資料庫**下拉式清單中，選取您要匯入 Siebel 的資料表的資料庫。  
  
   5.  按 [下一步] 。  
  
6. 在 **指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項。  
  
7. 在 **提供來源查詢**對話方塊方塊中，指定選取的查詢，以篩選要匯入到 SQL Server 的資料。 如需詳細資訊，選取 「 了解文法查詢[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，請參閱 < [Siebel 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。  
  
8. 若要驗證的查詢，請按一下**剖析**按鈕，再按一下**確定**中的快顯對話方塊中，然後按一下**下一步**。  
  
9. 在 **選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。 來源是您指定用來擷取 Siebel 的資料的查詢。 目的地會將 SQL Server 資料庫中建立的資料表。  
  
10. 精靈會建立預設的對應來源與目的地之間資料表欄位。 不過，您可以變更對應，根據您的需求。 若要變更欄位對應，請按一下**編輯對應**。  
  
11. 在 [**資料行對應**] 對話方塊中，您可以：  
  
    - 變更目的地資料表中的資料行的名稱。  
  
    - 忽略特定的目的地資料表中的資料行。  
  
    - 變更目的地資料表中的欄位資料類型。  
  
    - 變更其他欄位屬性，例如可為 null，大小、 有效位數和小數位數。  
  
    - 按一下 [確定] 。  
  
      ![Siebel 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")  
  
12. 在 **選取來源資料表和檢視表** 對話方塊中，按一下**下一步**。  
  
13. 在 **完成精靈**對話方塊方塊中，檢閱精靈將會執行，然後再按一下的動作的摘要**完成**。  
  
14. 在 [**正在執行作業**] 對話方塊中，精靈會啟動執行工作，以從 Siebel 將資訊匯入到 SQL Server 資料庫資料表。 每個工作的狀態會顯示在精靈中。  
  
15. 所有工作都成功都執行之後，請按一下**關閉**。 如果工作失敗，請參閱對應的錯誤訊息、 修正問題，並返回精靈。  
  
16. 精靈會將您的整合服務專案中的 SSIS 套件。 儲存整合服務專案。  
  
## <a name="run-the-ssis-package"></a>執行 SSIS 套件  
 封裝建立後的整合服務專案中，您可以將它 Siebel 系統的資料匯入到 SQL Server 資料庫執行。 執行下列步驟來執行封裝來匯入 Siebel 資料。  
  
1.  瀏覽至 [方案總管] 中的 SSIS 封裝。  
  
2.  以滑鼠右鍵按一下封裝名稱，然後按**執行封裝**。  
  
[執行 Integration Services (SSIS) 封裝](https://docs.microsoft.com/sql/integration-services/packages/run-integration-services-ssis-packages)提供詳細的資訊。 
  
## <a name="verify-the-results"></a>驗證結果  
 執行封裝之後, 您必須登入 SQL Server，並瀏覽至要匯入 Siebel 資料的資料庫驗證結果。 執行封裝應該已建立資料表的目的地資料庫中。 此資料表應該填入 Siebel 資料表中的值。  
  
## <a name="see-also"></a>另請參閱  
 [搭配使用 Data Provider for Siebel 與 SSIS](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)