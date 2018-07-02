---
title: 啟用驗證 Bank Identifier code |Microsoft Docs
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
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe33576bb23ff40fd80f85281c38a6f5a0ec930
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974167"
---
# <a name="enabling-validation-of-bank-identifier-codes"></a>啟用驗證 Bank Identifier code
Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]結構描述，請確定 「 銀行識別代碼 (BICs) SWIFT 交換文件中指定符合 SWIFT 定義 BIC 資料格式。 A4SWIFT 也支援驗證客戶指定 BIC 清單在資料庫中針對 BICs。  

 如果您有啟用 BRE 驗證，然後啟用 BIC 驗證，您可以執行這項驗證。  

 根據預設，A4SWIFT 安裝程式會停用 BRE 驗證。 若要啟用它，您必須設定 BRE 驗證組態參數設為 true，會使用 A4SWIFT 解譯器的接收管線。 您也必須執行 BRE 部署公用程式來將特定的驗證原則與主要原則部署到要驗證的訊息 (MT*xxx*_Master_policy.xml 和 MT*xxx*_Validation_Policy.xml)。 如需詳細資訊，請參閱 <<c0> [ 使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)並[部署 BRE 規則](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md)。  

 您已啟用 BRE 驗證之後，您必須使用發佈和部署這兩個 BIC 驗證原則 （BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml） 使用 「 規則引擎部署精靈 」。 再這麼做，您必須執行下列作業：  

- 來自 SWIFT 的 BIC 值資料庫中填入。 您可以使用的 Bicplus 資料表在 A4SWIFT 資料庫中，A4SWIFT 安裝程式已安裝，或您可以使用您自己自訂的資料庫。 如需詳細資訊，請參閱 <<c0> [ 管理 A4SWIFT 資料庫中的 Bicplus 資料表](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)。  

- BIC 資料庫設定並啟用 BIC 驗證自訂 BIC 主要原則。 請參閱下列程序。  

  為了達到最佳效能，您不應該部署 BIC 驗證原則如果 BIC 驗證不需要。  

> [!NOTE]
>  您可以發佈和部署 BIC 驗證原則，只有當您發佈 A4SWIFT_Codelist 和 A4SWIFT_Functions 詞彙。 執行 SWIFTSchemas 組件上的 BRE 部署公用程式，以發行這些詞彙。 如需詳細資訊，請參閱 <<c0> [ 第 1 課： 部署相關的商務規則](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)。  

### <a name="to-customize-the-bic-master-policy"></a>若要自訂 BIC 主要原則  

1. 開啟 XML 編輯器 （例如 [記事本])，並瀏覽至 **<*磁碟機*Program Files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則**。  

2. 開啟**BIC_Master_Policy.xml**。 以新的值取代下列現有的字串。  

   > [!NOTE]
   >  A4SWIFT 資料庫中的任一個的 Bicplus 資料表或您自己自訂的資料庫，您必須輸入值。 A4SWIFT 資料庫不在 BIC_Master_Policy.xml 是預設值。  

   > [!NOTE]
   >  下列字串不得包含雙引號括住。  

   |            現有的字串            |                                                              取代成                                                              |
   |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
   |      **指定 SQL SERVER 名稱**      | 名稱[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]包含保存 BIC 資料庫。 |
   |     **指定 BIC 資料庫名稱**     |                                         包含 BIC 資料表的資料庫名稱。                                          |
   | **指定整合式的安全性值** |                                                                **SSPI**                                                                |


3. 儲存已修改的主要原則。  

4. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**.  

5. 在 歡迎使用 頁面上，按一下**下一步**。  

6. 在部署工作 頁面上，按一下**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下**下一步**。  

7. 在原則存放區 頁面上，在**SQL Server 名稱**，選取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，其中包含 BizTalk 資料庫。 在 **選取的伺服器上的組態資料庫**，選取**BizTalkRuleEngineDb**，然後按一下 **下一步**。  

8. 在 匯入規則引擎原則/詞彙檔案 頁面中，瀏覽至 **<*磁碟機*files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFTMessages\A4SWIFT SRG\<版本\>\Base 原則**，按一下  **BIC_Master_Policy.xml**，按一下 **開啟**，然後按一下  **下一步**。  

9. 在準備就緒 頁面上，確認資料，然後**下一步**。  

10. 在匯入原則/詞彙 頁面上，確認命令成功，然後按一下**下一步**。  

11. 在正在完成規則引擎部署精靈 頁面中，按一下**再次執行此精靈**，然後按一下**完成**。  

12. 在 歡迎使用 頁面上，按一下**下一步**。  

13. 在部署工作 頁面上，按一下**部署原則**，然後按一下**下一步**。  

14. 在 **原則存放區**頁面上，於**SQL Server 名稱**，選取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，其中包含 BizTalk 資料庫。 在 **選取的伺服器上的組態資料庫**，選取**BizTalkRuleEngineDb**，然後按一下 **下一步**。  

15. 在 [**部署原則**頁面上，選取**BIC_Master_Policy.1.0**，然後按一下**下一步]**。  

16. 在 [**就緒**頁面上，按一下**下一步]**。  

17. 在部署原則 頁面中，如果已成功部署，按一下**下一步**。 按一下 **再次執行此精靈**，然後按一下**完成**。  

18. 重複步驟 5 至 17 **BIC_Validation_Policy.xml**、 輸入**BIC_Validation_Policy**而非**BIC_Master_Policy**。  

19. 結束 「 規則引擎部署精靈 」。  

20. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**商務規則編輯器 」**。 確認**原則**清單包含**BIC_Master_Policy**並**BIC_Validation_Policy**下**原則**。  

21. 依序展開**1.0 版-部署**下方**BIC_Master_Policy**，然後按一下**BIC_Master_Rule**。  

22. 在 [THEN] 窗格中，確認列出的 SQL 連線屬性正確無誤。  

    > [!NOTE]
    >  A4SWIFT 不會拾取對主要 BIC 驗證原則，直到您重新啟動裝載目前設定為使用 SWIFT 解譯器的接收管線的 BizTalk 服務的變更。 A4SWIFT 驗證通過此管線 BIC 值 BIC 主要原則中指定的 BIC 資料行中所包含的所有文件。 用以啟動此 BizTalk 服務 (BTSNTSvc.exe) 的使用者帳戶必須具有存取權的 BIC 資料庫和資料表。 為提升安全性，建議您授與至 BIC 資料庫和資料表的唯讀存取。  

    > [!NOTE]
    >  如果您使用 Message Repair 和 New Submission，World Wide Web Publishing 服務必須重新啟動 （藉由執行 iisreset.exe） 能夠從 InfoPath BIC 驗證。  

## <a name="see-also"></a>另請參閱  
 [使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)   
 [管理 A4SWIFT 資料庫中的 Bicplus 資料表](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)