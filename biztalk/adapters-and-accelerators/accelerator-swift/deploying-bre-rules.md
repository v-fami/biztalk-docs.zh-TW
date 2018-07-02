---
title: 部署 BRE 規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, BRE policies
- BRE policies, deploying
ms.assetid: 3a66aa57-e7f9-400f-963c-eda12fb1e659
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 311a15690dfa63fe18f67ce320310a0ed3339e6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977959"
---
# <a name="deploying-bre-rules"></a>部署 BRE 規則
您必須部署所用的 BRE 規則[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]協調流程以處理 SWIFT 的訊息。  

 **摘要**  

 發佈下列詞彙：  

- A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙。 這些都位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base Policies\Vocabulary。 發佈和部署這些使用 BRE 部署公用程式。  

  發佈和部署下列原則：  

- SWIFT 的訊息結構描述的基底原則，包括 SWIFT_Reference_Policy.xml、 SWIFT_PartyIdentifier_Policy.xml，以及網路規則原則 (SWIFT_NetworkRulexxx_Policy.xml) 部署結構描述。 這些都位於\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則。 發佈和部署這些使用 BRE 部署公用程式。  

- 與已部署的訊息結構描述 （MTxxx_Master_Policy.xml 和 MTxxx_Validation_Policy.xml） 相關聯的主要和驗證原則。 這些都位於\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MTxxx。 發佈和部署這些使用 BRE 部署公用程式。  

- 若需要 BIC 驗證，與 BIC 驗證 （BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml） 相關聯的主要和驗證原則。 這些都位於\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則。 發佈和部署這些原則時，您必須使用的 SQL Server、 BIC 資料庫名稱，名稱來自訂 BIC_Master_Policy.xml 前後整合的安全性值。 如需詳細資訊，請參閱 <<c0> [ 啟用驗證的銀行識別代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。 發佈和部署這些使用規則引擎部署精靈。  

### <a name="to-deploy-bre-rules"></a>若要部署 BRE 規則  

1.  執行 BRE 部署公用程式。 如需詳細資訊，請參閱 「 部署 BRE 規則所有在一次 」 下方。 此公用程式將會發行並部署下列：  

    -   A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙  

    -   SWIFT 的訊息結構描述，包括 SWIFT_Reference_Policy.xml、 SWIFT_PartyIdentifier_Policy.xml，以及網路規則原則 (SWIFT_NetworkRulexxx_Policy.xml) 的基底原則  

    -   與已部署的訊息結構描述 （MTxxx_Master_Policy.xml 和 MTxxx_Validation_Policy.xml） 相關聯的主要和驗證原則  

2.  自訂 BIC_Master_Policy.xml SQL server、 BIC 資料庫名稱，以及整合式安全性值的名稱。 如需詳細資訊，請參閱 <<c0> [ 啟用驗證的銀行識別代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。  

3.  執行規則引擎部署精靈來發佈和部署 BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml (在\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則)。 如需詳細資訊，請參閱 「 部署 BRE 規則一次 」 下方。  

## <a name="tools-for-deploying-the-policies"></a>部署原則的工具  
 發佈的詞彙和部署原則的最簡單方式是使用 「 商務規則引擎 (BRE) 部署公用程式 A4SWIFT 軟體開發套件 (SDK) 中。 您也可以執行，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]規則引擎部署精靈，它會執行一次的相同工作的一個詞彙或原則。  

> [!NOTE]
>  BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。 您必須部署這些使用規則引擎部署精靈。  

### <a name="deploying-bre-rules-all-at-once"></a>全部一次部署 BRE 規則  
 商務規則引擎 (BRE) 部署公用程式在一個步驟中執行一系列的發行和部署工作。 您必須重新執行部署公用程式任何時候將結構描述新增至您的專案。  

##### <a name="to-deploy-bre-rules-using-the-bre-deployment-utility"></a>部署 BRE 規則使用 BRE 部署公用程式  

1. 按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**.  

2. 在 [BRE 部署公用程式] 對話方塊中，按一下**瀏覽**。  

3. 在.NET 全域組件快取 對話方塊中，選取您在部署的專案組[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)，然後按一下**確定**。  

4. 在 [BRE 部署公用程式] 對話方塊中，按一下**部署**。  

   > [!NOTE]
   >  根據您部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行與 BRE 搭配使用。 完成時，BRE 部署公用程式會顯示下列訊息：  

   > [!NOTE]
   >  「 部署已完成。 檢視記錄檔或商務規則編輯器 」 的詳細資料。 」  

5. 關閉 [BRE 部署公用程式] 對話方塊。  

6. 開啟[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管。 瀏覽至\<*磁碟機*\>: \Documents and Settings\All Users\Application Data，並確認記錄檔 BREDeploymentLog.txt 出現在該磁碟機。  

7. 重新啟動 「 規則引擎更新服務。 這樣做，即可**開始**，再按一下**執行**，輸入**services.msc**，，然後按一下**確定**。 在 [**服務 （本機）** ] 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下**重新啟動**。  

### <a name="deploying-bre-rules-one-at-a-time"></a>部署 BRE 規則一次  
 您可以使用 「 規則引擎部署精靈 」 來發佈詞彙，並將原則一部署一次。 一種詞彙，此程序牽涉到匯入和發佈的詞彙至資料庫，從一個步驟中的檔案。 原則，此程序牽涉到匯入和發佈原則，在一個步驟中，然後將它部署在另一個步驟。  

##### <a name="to-deploy-bre-rules-using-the-rules-engine-deployment-wizard"></a>使用規則引擎部署精靈部署 BRE 規則  

1. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**.  

2. 在歡迎使用 規則引擎部署精靈 頁面中，按一下**下一步**。  

3. 在部署工作 頁面上，按一下**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下**下一步**。  

4. 在原則存放區 頁面上，在**SQL Server 名稱清單**，選取您的伺服器，然後在**選取的伺服器上的組態資料庫**清單中，選取**BizTalkRuleEngineDb**。 按 [下一步] 。  

5. 在 匯入規則引擎原則/詞彙檔案 頁面中，按一下 **瀏覽**。  

6. 在匯入原則檔案 頁面上，從在**查看**下拉式清單中，移至下列資料夾，視詞彙或原則的其中一個：  

   -   \<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>A4SWIFT_CodeLists.xml 的 \Base Policies\Vocabulary和 A4SWIFT_Functions.xml  

   -   \<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base SWIFT_Reference_Policy.xml，SWIFT_ 原則PartyIdentifier_Policy.xml、 網路規則原則、 BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml  

   -   \<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MTxxx master 和驗證原則已部署的訊息結構描述相關聯  

7. 選取您想要部署，然後按一下 原則**開啟**。  

8. 在 [匯入規則引擎原則/詞彙檔案] 頁面中，按一下 [**下一步]**。  

9. 在 [就緒] 頁面中，按一下 [**下一步]**。  

10. 在匯入原則/詞彙 頁面上，確認命令成功，然後按一下**下一步**。  

11. 如果您想要部署原則時，在正在完成規則引擎部署精靈 頁面中，按一下**再次執行此精靈**，然後按一下**完成**。  

12. 在歡迎使用 規則引擎部署精靈 頁面中，按一下**下一步**。  

13. 在部署工作 頁面上，按一下**部署原則**，然後按一下**下一步**。  

14. 在原則存放區 頁面上，在**SQL Server 名稱清單**，選取您的伺服器，然後在**選取的伺服器上的組態資料庫**清單中，選取**BizTalkRuleEngineDb**。 按 [下一步] 。  

15. 在部署原則 頁面上，按一下向下箭號旁**規則引擎原則**文字方塊中，選取您剛才的原則，發佈，然後按一下**下一步**。  

16. 在 [就緒] 頁面中，按一下 [**下一步]**。  

17. 在 [**匯入原則/詞彙**頁面上，確認命令成功，然後按一下**下一步]**。  

18. 按一下 **[完成]**。  

19. 重新啟動**規則引擎更新服務**。 這樣做，即可**開始**，再按一下**執行**，輸入**services.msc**，，然後按一下**確定**。 在 [**服務 （本機）** ] 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下**重新啟動**。
