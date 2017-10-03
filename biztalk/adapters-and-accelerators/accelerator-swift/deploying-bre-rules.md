---
title: "部署 BRE 規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, BRE policies
- BRE policies, deploying
ms.assetid: 3a66aa57-e7f9-400f-963c-eda12fb1e659
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195b63948f79ed5403c130048aae86f7e7422c96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-bre-rules"></a>部署 BRE 規則
您必須部署所用的 BRE 規則[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理 SWIFT 訊息的協調流程。  
  
 **摘要**  
  
 發行下列詞彙：  
  
-   A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙。 這些都位於*\<磁碟機 >*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Base Policies\詞彙。 發行和部署這些使用 BRE 部署公用程式。  
  
 發佈和部署下列原則：  
  
-   SWIFT 訊息結構描述的基底原則，包括 SWIFT_Reference_Policy.xml、 SWIFT_PartyIdentifier_Policy.xml，以及網路規則原則 (SWIFT_NetworkRulexxx_Policy.xml) 部署結構描述。 這些都位於\<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Base 原則。 發行和部署這些使用 BRE 部署公用程式。  
  
-   與已部署的訊息結構描述 （MTxxx_Master_Policy.xml 和 MTxxx_Validation_Policy.xml） 相關聯的主要和驗證原則。 這些都位於\<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Category 1\MTxxx。 發行和部署這些使用 BRE 部署公用程式。  
  
-   若需要 BIC 驗證 BIC 驗證 （BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml） 與相關聯的主要和驗證原則。 這些都位於\<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Base 原則。 發佈和部署這些原則，您必須自訂 BIC_Master_Policy.xml 的 SQL Server、 BIC 資料庫名稱，名稱前後整合安全性值。 如需詳細資訊，請參閱[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。 發行和部署這些使用規則引擎部署精靈。  
  
### <a name="to-deploy-bre-rules"></a>若要部署 BRE 規則  
  
1.  執行 BRE 部署公用程式。 如需詳細資訊，請參閱 「 部署 BRE 規則所有在一次 」 底下。 此公用程式將會發行，並部署下列：  
  
    -   A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙  
  
    -   SWIFT 的訊息結構描述，包括 SWIFT_Reference_Policy.xml、 SWIFT_PartyIdentifier_Policy.xml，以及網路規則原則 (SWIFT_NetworkRulexxx_Policy.xml) 的基底原則  
  
    -   與已部署的訊息結構描述 （MTxxx_Master_Policy.xml 和 MTxxx_Validation_Policy.xml） 相關聯的主要和驗證原則  
  
2.  自訂 BIC_Master_Policy.xml SQL server、 BIC 資料庫名稱，以及整合式安全性值的名稱。 如需詳細資訊，請參閱[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。  
  
3.  執行規則引擎部署精靈來發行和部署 BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml (在\<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFTMessages\A4SWIFT-SRG\<版本 > \Base 原則)。 如需詳細資訊，請參閱 「 部署 BRE 規則一個在時間 」 底下。  
  
## <a name="tools-for-deploying-the-policies"></a>部署原則的工具  
 發佈詞彙及部署原則的最簡單方式是使用 「 商務規則引擎 (BRE) 部署公用程式 A4SWIFT 軟體開發套件 (SDK) 中。 您也可以執行動作，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]規則引擎部署精靈 」 便會執行相同工作的一個詞彙或原則一次。  
  
> [!NOTE]
>  BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。 您必須部署這些使用規則引擎部署精靈。  
  
### <a name="deploying-bre-rules-all-at-once"></a>一次部署 BRE 規則  
 商務規則引擎 (BRE) 部署公用程式在一個步驟中執行一系列的發行和部署工作。 您必須重新執行部署公用程式隨時將結構描述加入至您的專案。  
  
##### <a name="to-deploy-bre-rules-using-the-bre-deployment-utility"></a>若要部署使用 BRE 部署公用程式的 BRE 規則  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**.  
  
2.  在 BRE 部署公用程式 對話方塊中，按一下 **瀏覽**。  
  
3.  在.NET 全域組件快取] 對話方塊中，選取您在部署專案組件[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)，然後按一下 [**確定**。  
  
4.  在 BRE 部署公用程式 對話方塊中，按一下 **部署**。  
  
    > [!NOTE]
    >  根據您部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行 BRE 搭配使用。 完成時，BRE 部署公用程式會顯示下列訊息：  
  
    > [!NOTE]
    >  「 已完成部署。 檢視記錄檔或商務規則編輯器 」 以取得詳細資料。 」  
  
5.  關閉 [BRE 部署公用程式] 對話方塊。  
  
6.  開啟[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管。 瀏覽至\<*磁碟機*>: \Documents and Settings\All Users\Application 資料，並確認記錄檔 BREDeploymentLog.txt 出現在該磁碟機。  
  
7.  重新啟動 「 規則引擎更新服務。 這樣即可**啟動**，然後按一下**執行**、 輸入**services.msc**，然後按一下**[確定]**。 在**服務 （本機）**視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。  
  
### <a name="deploying-bre-rules-one-at-a-time"></a>部署 BRE 規則一次  
 您可以使用 「 規則引擎部署精靈 」 來發佈詞彙和部署原則一次。 一種詞彙，這個程序牽涉到匯入和資料庫發佈的詞彙，從一個步驟中的檔案。 原則的程序牽涉到匯入與發行原則在一個步驟中，然後將其部署在另一個步驟。  
  
##### <a name="to-deploy-bre-rules-using-the-rules-engine-deployment-wizard"></a>若要部署 BRE 規則使用 規則引擎部署精靈  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**.  
  
2.  在歡迎使用規則引擎部署精靈] 頁面上，按一下 [**下一步**。  
  
3.  在部署工作 頁面上，按一下 **匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。  
  
4.  在原則存放區 頁面上，在**SQL 伺服器名稱 清單**，選取您的伺服器，然後在**選取的伺服器上設定資料庫**清單中，選取**BizTalkRuleEngineDb**。 按一下 **[下一步]**。  
  
5.  在 匯入規則引擎原則/詞彙檔案 頁面中，按一下 **瀏覽**。  
  
6.  在匯入原則檔案 頁面上，從在**查看**下拉式清單中，移至下列資料夾，根據的詞彙或原則的其中一個：  
  
    -   \<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml \Base Policies\Vocabulary  
  
    -   \<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Base SWIFT_Reference_Policy.xml，SWIFT_PartyIdentifier_Policy.xml，原則網路規則原則、 BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml  
  
    -   \<磁碟機 >: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Category 1\MTxxx 與已部署的訊息相關聯的主要和驗證原則結構描述  
  
7.  選取您想要部署，然後按一下 原則**開啟**。  
  
8.  在 匯入規則引擎原則/詞彙檔案 頁面中，按一下 **下一步**。  
  
9. 在 就緒 頁面上，按一下 **下一步**。  
  
10. 在 匯入原則/詞彙 頁面上，確認命令成功，然後按一下 **下一步**。  
  
11. 如果您想要部署原則，在正在完成規則引擎部署精靈 頁面上，按一下 **再次執行此精靈**，然後按一下 **完成**。  
  
12. 在歡迎使用規則引擎部署精靈] 頁面上，按一下 [**下一步**。  
  
13. 在部署工作 頁面上，按一下 **部署原則**，然後按一下 **下一步**。  
  
14. 在原則存放區 頁面上，在**SQL 伺服器名稱 清單**，選取您的伺服器，然後在**選取的伺服器上設定資料庫**清單中，選取**BizTalkRuleEngineDb**。 按一下 **[下一步]**。  
  
15. 在部署原則 頁面上，按一下向下箭號旁**規則引擎原則** 文字方塊中，選取您剛才的原則，發佈，然後按一下**下一步**。  
  
16. 在 就緒 頁面上，按一下 **下一步**。  
  
17. 在**匯入原則/詞彙**頁面上，確認命令成功，然後按一下 **下一步**。  
  
18. 按一下 **[完成]**。  
  
19. 重新啟動**規則引擎更新服務**。 這樣即可**啟動**，然後按一下**執行**、 輸入**services.msc**，然後按一下**[確定]**。 在**服務 （本機）**視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。