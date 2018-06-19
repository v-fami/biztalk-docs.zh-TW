---
title: 第 1 課： 部署相關的商務規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, deploying
- deploying, business rules
ms.assetid: f8f5b103-4b66-4836-8165-99692574961a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17c4b470b802a980306481361c1fafcec4f70269
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960764"
---
# <a name="lesson-1-deploying-the-related-business-rules"></a>第 1 課： 部署相關的商務規則
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]包含程式在 A4SWIFT 軟體開發套件 (SDK) 稱為 「 商務規則引擎 (BRE) 部署公用程式。 在這一課，您可以使用此公用程式檢查組件以取得部署的結構描述、 決定所需的規則，及部署必要的詞彙和每個結構描述的原則。  
  
 您也可以使用 SWIFT 標準發行指南 (SRG) 來識別所需的規則，然後使用商務規則編輯器 」 工具來部署的詞彙和原則部署的規則。  
  
### <a name="to-deploy-the-related-business-rules"></a>若要部署的相關的商務規則  
  
1.  按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**。  
  
2.  在 BRE 部署公用程式 對話方塊中，按一下 **瀏覽**。  
  
3.  在.NET 全域組件快取] 對話方塊中，選取**SWIFTSchemas**，然後按一下 [**確定**。  
  
    > [!NOTE]
    >  SWIFTSchemas 參考組件您先前部署。  
  
4.  按一下**部署**。  
  
     根據您部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行 BRE 搭配使用。 完成時，BRE 部署公用程式會顯示下列訊息：  
  
     **部署已完成。如需詳細資訊，檢視記錄檔或商務規則編輯器 」。**  
  
5.  關閉 SWIFT BRE 部署公用程式的對話方塊。  
  
6.  在 Windows 檔案總管，瀏覽至\<*磁碟機*\>: \Documents and Settings\All Users\Application 資料，確認記錄檔**BREDeploymentLog.txt**會出現在資料夾。  
  
    > [!NOTE]
    >  您可以開啟記錄檔，以確認部署步驟的每個使用文字編輯器。  
  
7.  重新啟動 「 規則引擎更新服務。 這樣即可**啟動**，然後按一下**執行**、 輸入**services.msc**，然後按一下 **[確定]**。 在**服務 （本機）** 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。  
  
 若要繼續[第 2 課： 確認部署使用 「 商務規則編輯器 」 工具](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)。