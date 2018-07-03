---
title: 升級 BizTalk Accelerator for SWIFT |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede2af21-4c7d-4f9e-b255-1ada86eda68d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa934db02ba9f82134acd5c86da17c6ea240706e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008215"
---
# <a name="upgrade-biztalk-accelerator-for-swift"></a>升級 BizTalk Accelerator for SWIFT
升級[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]BizTalk 伺服器上。 

### <a name="before-you-upgrade"></a>升級之前

* 執行升級的使用者必須是 BizTalk Server 系統管理員群組的成員。
* 當您執行時，就必須執行 SQL Server (MSSQLSERVER) 服務[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]升級。
* 請勿執行無訊息安裝來升級為 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]。
* 升級 BizTalk Server 中，然後再升級[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]。
* 必須安裝 BizTalk Server 執行階段[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]安裝及其執行階段元件的升級。 如果之前未安裝 BizTalk Server 執行階段[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]升級，則[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]元件不會安裝，並會移除先前的組件從全域組件快取 (GAC) 中。
* 當您安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]，MessagePack 已安裝。 MessagePack 任何現有版本會取代在升級期間。
* 升級至[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]藉由執行[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]安裝。 安裝程式可讓您移轉現有[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]組態資訊。 
* 任何已被取代的功能的資料夾和捷徑，升級可能不會移除。

## <a name="supported-upgrade-paths"></a>支援的升級路徑  
 下表列出支援[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]可以升級的版本。 「 是 」 表示該版本可以升級。 「 否 」 表示該版本無法升級。 如果[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]版本中沒有列出，該版本無法升級。  


|                                                                                                       | [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] | BizTalk Server 2013 |
|-------------------------------------------------------------------------------------------------------|------------------------------------------------------|-------------------------------------------------------|---------------------|
| [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 2013 |                         是                          |                          是                          |         否          |
| [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 2010 |                          否                          |                          是                          |         是         |

## <a name="upgrade-a4swift"></a>升級 A4SWIFT

1. 備份[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]資料庫和您 SWIFT 訊息結構描述。 安裝程式升級[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]資料庫。

2. 備份中的任何檔案`%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT`和`%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT MessagePack`已更新的資料夾。
  
3. 解除部署任何專案、 BizTalk 成品或有任何參考的組件[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]MessagePack 組件。

4. 在 Visual Studio 中，依下列順序手動解除部署所有的 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] 組件：

* Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration
* Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas
* Microsoft.Solutions.FinancialServices.SWIFT.MrsrService
* Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas。

5. 執行[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]安裝程式以升級。

> [!NOTE]
> 當您升級[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]，升級會移除存取權限**A4SWIFT Administrators**並**A4SWIFT 使用者**群組從`%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT\Service`資料夾。         
        
## <a name="post-upgrade-steps"></a>升級後步驟

1. 使用[BTSTask.exe](../../core/btstask-command-line-reference.md) (%programfiles%\Microsoft BizTalk Server)，以手動方式重新部署 A4SWIFT 組件，以下列順序：
2. Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas
3. Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration

     > [!NOTE]
     > 您不需要重新部署`Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas`。 安裝重新部署此組件。

     > [!IMPORTANT] 
     > 重建和重新部署您的結構描述專案，在上一個步驟中，刪除較舊版本的前`A4SWIFT Base Types.xsd`和`SWIFT Common Data Types.xsd`從結構描述專案中，取代訊息組件版本，這些結構描述，然後建置並部署結構描述專案。 如果您不會取代這些結構描述，您將無法建置和部署結構描述專案。

4. 重建並部署任何專案或您使用較舊版本的組件[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]或訊息組件。
5. 如果您已對 SWIFT 訊息組件的結構描述的任何變更，這些變更在新的訊息組件結構描述，然後建置並部署這些結構描述。
6. 解除部署任何現有的 BRE 原則的已安裝舊版的[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]。 然後安裝及部署從較新的對應原則[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]安裝檔案。 您可以手動或透過**BREDeployment**工具。

   > [!NOTE]
   > 即使[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]升級不會使用 「 商務規則引擎 (BRE) 」 功能造成任何問題，我們建議您取代舊版的[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]BRE 原則的最新的訊息組件 BRE 原則，某些 BRE 原則取得已更新每個訊息組件。
    
7. 如果您在自訂中的任何檔案`%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT`資料夾，然後為較新版本中進行相同變更。
8. 移除**a4swift_limited** db_denydatareader 角色，如下所示的成員身分：
    1. 開啟 SQL Server Management Studio。 在 Management Studio 中，依序展開**資料庫**，展開**BizTalk Accelerator for SWIFT**，然後選取**角色**。
    2. 按兩下**a4swift_limited**。 選取 **權限**，並檢查 SELECT`Bic11`和`Bic10`。 選取 **確定**，接著關閉屬性。
    3. 按兩下**db_denydatareader**。 在 [使用者] 欄位中，選取**a4swift_limited**，然後選取**移除**。 選取 [確定]。

9. 執行 QFERollUpDBUpdate 指令碼：

    > [!NOTE]
    > 您必須是隸屬**A4Swift 管理員**執行 QFERollUpDBUpdate 指令碼的群組。
    
   1. 開啟 SQL Server Management Studio。 在 Management Studio 中，按一下 新增查詢。 
   2. 選取[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]從下拉式清單中的資料庫。 
   3. 在 Windows 檔案總管中，移至`%programfiles%\Microsoft BizTalk <version> Accelerator for SWIFT\Scripts`，然後將拖曳**QFERollUpDBUpdate.sql**檔案拖曳至新的 [查詢] 窗格中，然後按**Execute**。
    
    
## <a name="upgrading-in-a-multi-server-environment"></a>多伺服器環境中升級

在多伺服器[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]環境中的，所有伺服器上，升級 BizTalk Server 中，然後再升級[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]。 請依下列順序移轉您的伺服器：

* 裝載 BizTalk 群組的伺服器
* 每個處理節點
* BAM 入口網站伺服器


## <a name="next-steps"></a>後續的步驟
[設定 BizTalk Accelerator for SWIFT ](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)