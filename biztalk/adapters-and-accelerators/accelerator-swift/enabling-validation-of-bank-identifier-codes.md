---
title: 啟用驗證的銀行識別項代碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Bank Identifier Code (BIC), enabling
ms.assetid: d268a892-f304-44cb-b590-28ef359c8d99
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3868906d4f61242b1344a02147e4e71307d67d3
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="enabling-validation-of-bank-identifier-codes"></a>啟用驗證的銀行識別項代碼
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] 結構描述，請確定銀行識別項代碼 (BICs) SWIFT 交換文件中指定符合 SWIFT 定義 BIC 資料格式。 A4SWIFT 也支援驗證針對資料庫中客戶指定 BIC 清單 BICs。  
  
 如果您有啟用 BRE 驗證，然後再啟用 BIC 驗證，您可以執行這項驗證。  
  
 根據預設，A4SWIFT 安裝程式會停用 BRE 驗證。 若要啟用它，您必須為 true，會使用 A4SWIFT 解譯器的接收管線設定 BRE 驗證組態參數。 您也必須執行 BRE 部署公用程式來主要原則和特定的驗證原則部署到要驗證的訊息 (MT*xxx*_Master_policy.xml 和 MT*xxx*_Validation_Policy.xml)。 如需詳細資訊，請參閱[使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)和[部署 BRE 規則](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md)。  
  
 您已啟用 BRE 驗證之後，您必須使用發行和部署這兩個 BIC 驗證原則 （BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml） 使用 「 規則引擎部署精靈 」。 在進行之前，您必須執行下列作業：  
  
-   填入資料庫與來自 SWIFT BIC 值。 您可以使用 Bicplus 資料表在 A4SWIFT 資料庫中，A4SWIFT 安裝程式已安裝，或您可以使用您自己自訂的資料庫。 如需詳細資訊，請參閱[管理 Bicplus 資料庫中的資料表 A4SWIFT](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)。  
  
-   BIC 資料庫設定和啟用 BIC 驗證 BIC 主要原則自訂。 請參閱下列程序。  
  
 為提升效能，您如果不應部署 BIC 驗證原則不需要 BIC 驗證。  
  
> [!NOTE]
>  您可以發行和部署 BIC 驗證原則，只有當您已經發行 A4SWIFT_Codelist 和 A4SWIFT_Functions 詞彙。 發行這些詞彙 SWIFTSchemas 組件上執行 BRE 部署公用程式。 如需詳細資訊，請參閱[第 1 課： 部署相關的商務規則](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)。  
  
### <a name="to-customize-the-bic-master-policy"></a>若要自訂 BIC 主要原則  
  
1.  開啟 XML 編輯器 （例如 [記事本])，並瀏覽至 **<*磁碟機*Program Files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則**。  
  
2.  開啟**BIC_Master_Policy.xml**。 下列現有的字串取代為新值。  
  
    > [!NOTE]
    >  您必須輸入值 A4SWIFT 資料庫中的任一個 Bicplus 資料表，或您自己自訂的資料庫。 A4SWIFT 資料庫不 BIC_Master_Policy.xml 中的預設值。  
  
    > [!NOTE]
    >  下列字串必須不包含雙引號括住。  
  
    |現有的字串|取代成|  
    |---------------------|------------------|  
    |**指定 SQL SERVER 名稱**|名稱[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]包含保存 BIC 資料庫。|  
    |**指定 BIC 資料庫名稱**|包含 BIC 資料表的資料庫名稱。|  
    |**指定整合式的安全性值**|**SSPI**|  
  
3.  儲存修改過的主要原則。  
  
4.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**.  
  
5.  在 歡迎使用 頁面上，按一下 **下一步**。  
  
6.  在部署工作 頁面上，按一下 **匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。  
  
7.  在原則存放區 頁面上，在**SQL Server 名稱**，選取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，其中包含 BizTalk 資料庫。 在**選取的伺服器上設定資料庫**，選取**BizTalkRuleEngineDb**，然後按一下 **下一步**。  
  
8.  在 匯入規則引擎原則/詞彙檔案 頁面中，瀏覽至 **<*磁碟機*files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFTMessages\A4SWIFT SRG\<版本\>\Base 原則**，按一下  **BIC_Master_Policy.xml**，按一下 **開啟**，然後按一下  **下一步**。  
  
9. 在上就緒] 頁面上，確認資料，然後按一下 [**下一步**。  
  
10. 在 匯入原則/詞彙 頁面上，確認命令成功，然後按一下 **下一步**。  
  
11. 在正在完成規則引擎部署精靈 頁面上，按一下 **再次執行此精靈**，然後按一下 **完成**。  
  
12. 在 歡迎使用 頁面上，按一下 **下一步**。  
  
13. 在部署工作 頁面上，按一下 **部署原則**，然後按一下 **下一步**。  
  
14. 在**原則存放區**頁面上，於**SQL Server 名稱**，選取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，其中包含 BizTalk 資料庫。 在**選取的伺服器上設定資料庫**，選取**BizTalkRuleEngineDb**，然後按一下 **下一步**。  
  
15. 在**部署原則**頁面上，選取**BIC_Master_Policy.1.0**，然後按一下 **下一步**。  
  
16. 在**準備**頁面上，按一下**下一步**。  
  
17. 在部署原則 頁面中，如果部署成功後，按一下**下一步**。 按一下**再次執行此精靈**，然後按一下 **完成**。  
  
18. 重複步驟 5 至 17 **BIC_Validation_Policy.xml**、 輸入**BIC_Validation_Policy**而不是**BIC_Master_Policy**。  
  
19. 結束 「 規則引擎部署精靈 」。  
  
20. 按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。 確認**原則**清單包含**BIC_Master_Policy**和**BIC_Validation_Policy**下**原則**。  
  
21. 展開**版本 1.0 – 已部署**下**BIC_Master_Policy**，然後按一下  **BIC_Master_Rule**。  
  
22. 在 [THEN] 窗格中，確認列出的 SQL 連線屬性正確無誤。  
  
    > [!NOTE]
    >  A4SWIFT 不會拾取對主要 BIC 驗證原則，直到您重新啟動裝載目前設定為使用 SWIFT 解譯器的接收管線的 BizTalk 服務的變更。 A4SWIFT 驗證通過此管線 BIC 值 BIC 主要原則中指定的 BIC 資料行中所包含的所有文件。 用來啟動此 BizTalk 服務 (BTSNTSvc.exe) 的使用者帳戶必須具有存取權的 BIC 資料庫和資料表。 為提升安全性，建議您將授與 BIC 資料庫和資料表的唯讀存取。  
  
    > [!NOTE]
    >  如果您使用 Message Repair 和 New Submission，World Wide Web Publishing 服務必須重新啟動 （藉由執行 iisreset.exe） BIC 驗證才能從 InfoPath 工作。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)   
 [管理 A4SWIFT 資料庫中的 Bicplus 資料表](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)