---
title: BRE 部署公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BRE Deployment utility
- deploying, BRE Deployment utility
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b2449795a52bd26bed0326a3aa2fcf57f8bb552
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010151"
---
# <a name="bre-deployment-utility"></a>BRE 部署公用程式
您可以使用 BRE 部署公用程式來發佈和部署的商務規則引擎 (BRE) 詞彙和原則所需的 SWIFT 結構描述。 發行和部署這些詞彙和原則，才能啟用 BRE 驗證之訊息類型。  
  
 您也可以部署 商務規則來識別所需的規則，使用 SWIFT 標準版指南 (SRGs)，然後使用 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]部署原則與詞彙的商務規則編輯器 」 工具。 不過，使用 BRE 部署公用程式會更加容易。  
  
 BRE 部署公用程式會產生下列結果：  
  
- 檢查您指定的部署組件，並判斷您部署組件的訊息結構描述。  
  
- 發佈[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml 並[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml 詞彙所需的 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]商務規則處理。  
  
- 發佈和部署 SWIFT 基底 （參考原則、 合作對象識別項原則，以及網路規則原則） 相關聯的原則與訊息結構描述。  
  
- 發佈和部署的主要原則和與每個訊息結構描述相關聯的驗證原則。  
  
- 產生記錄檔，指出所需的所有步驟。 這個檔案是在 BREDeploymentLog.txt \<*磁碟機*\>: \Documents and Settings\All Users\Application Data 資料夾。  
  
  > [!NOTE]
  >  BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。 您必須部署這些使用規則引擎部署精靈。  
  > 
  > [!NOTE]
  >  如果您已安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]在非預設目錄 (C:\Program Files\Microsoft 以外[!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)])，或您正在 64 位元電腦上，BRE 部署公用程式將無法正常運作之前變更中的路徑過的 BREDeployment.exe.config 檔案。 此組態檔位於\<*磁碟機*\>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools 資料夾。 若要更新公用程式的組態，在 [記事本] 開啟過的 BREDeployment.exe.config 並變更詞彙目錄、 結構描述，以及基底原則的資料夾。  
  
  您也可以使用部署公用程式，若要反轉此程序，解除部署和取消發佈原則和詞彙。 公用程式都已部署，並解除部署功能。  
  
### <a name="to-use-the-bre-deployment-utility"></a>若要使用 BRE 部署公用程式  
  
1.  按一下 **開始**，指向**程式**，指向**Microsoft BizTalk Accelerator for SWIFT**，然後按一下**BRE 部署公用程式**。  
  
2.  BRE 部署公用程式中，按一下**瀏覽**。  
  
3.  選取您要發行部署的詞彙和原則]，然後按一下 [組件的已部署的組件**確定**。  
  
4.  按一下 **部署**。  
  
    > [!NOTE]
    >  根據您部署與該組件的結構描述，BRE 部署公用程式會經歷找出相關的規則，並將其發佈用於 BRE 的程序。 完成時，BRE 部署公用程式會顯示下列訊息：**完成部署之後**。 若要確認成功部署使用 「 商務規則編輯器 」。  
  
    > [!NOTE]
    >  若要解除部署原則和詞彙，按一下**Undeploy**。 解除部署處理程序不會不會解除部署 A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙，這可能會由其他已部署的原則。  
  
5.  找出\<*磁碟機*\>: \Documents and Settings\All Users\Application Data，若要確認此公用程式建立記錄檔檔案 BREDeploymentLog.txt。  
  
    > [!NOTE]
    >  您可以確認每個部署步驟中使用文字編輯器中開啟記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../adapters-and-accelerators/accelerator-swift/tools.md)