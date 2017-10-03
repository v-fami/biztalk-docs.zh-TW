---
title: "BRE 部署公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE Deployment utility
- deploying, BRE Deployment utility
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f40a75d898369cfc730ba5cb4f25c199e1333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bre-deployment-utility"></a>BRE 部署公用程式
您可以使用 BRE 部署公用程式來發佈和部署的商務規則引擎 (BRE) 詞彙和 SWIFT 的結構描述所需的原則。 發行和部署這些詞彙和原則，才能啟用 BRE 驗證之訊息類型。  
  
 您也可以部署商務規則，以識別所需的規則，使用 SWIFT 標準發行指南 (SRGs)，然後使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]商務規則編輯器 」 工具來部署原則與詞彙。 不過，使用 BRE 部署公用程式會比較容易。  
  
 BRE 部署公用程式會產生下列結果：  
  
-   檢查您指定的已部署組件，並判斷您部署組件的訊息結構描述。  
  
-   發行[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml 詞彙所需的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]商務規則處理。  
  
-   發行和部署 SWIFT 基底 （參考原則、 合作對象識別項原則，以及網路規則原則） 相關聯的原則與訊息結構描述。  
  
-   部署主要原則和每個訊息結構描述相關聯的驗證原則和發佈。  
  
-   產生記錄檔，指出所需的所有步驟。 這個檔案是在 BREDeploymentLog.txt \<*磁碟機*>: \Documents and Settings\All Users\Application Data 資料夾。  
  
    > [!NOTE]
    >  BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。 您必須部署這些使用規則引擎部署精靈。  
  
    > [!NOTE]
    >  如果您已安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]非預設的目錄 (C:\Program Files\Microsoft 以外[!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)])，或您使用 64 位元電腦上，BRE 部署公用程式將無法正常運作之前變更中的路徑過的 BREDeployment.exe.config 檔案。 此組態檔位於\<*磁碟機*>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools 資料夾。 若要更新公用程式的組態，在 [記事本] 中開啟過的 BREDeployment.exe.config 並變更詞彙目錄、 結構描述，以及基底原則資料夾。  
  
 您也可以使用部署公用程式可反轉程序中，解除部署和取消發佈原則和詞彙。 公用程式都有部署和解除部署功能。  
  
### <a name="to-use-the-bre-deployment-utility"></a>若要使用 BRE 部署公用程式  
  
1.  按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**。  
  
2.  BRE 部署公用程式中，按一下 **瀏覽**。  
  
3.  選取您要發佈的詞彙和原則，部署，然後按一下 組件的部署的組件**確定**。  
  
4.  按一下**部署**。  
  
    > [!NOTE]
    >  根據您部署與該組件的結構描述，BRE 部署公用程式就會進行識別相關的規則，然後發行 BRE 搭配使用的程序。 完成時，BRE 部署公用程式會顯示下列訊息：**完成部署之後**。 若要確認成功部署使用 「 商務規則編輯器 」。  
  
    > [!NOTE]
    >  若要解除部署原則和詞彙，請按一下**解除部署**。 解除部署處理程序解除 A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙，這可能需要使用其他已部署的原則未部署。  
  
5.  找出\<*磁碟機*>: \Documents and Settings\All Users\Application 資料，以確認公用程式建立記錄檔檔案 BREDeploymentLog.txt。  
  
    > [!NOTE]
    >  您可以使用文字編輯器，以確認每個部署步驟來開啟記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../adapters-and-accelerators/accelerator-swift/tools.md)