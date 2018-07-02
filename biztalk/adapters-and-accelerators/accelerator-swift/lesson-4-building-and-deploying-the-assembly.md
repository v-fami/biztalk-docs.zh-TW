---
title: 第 4 課： 建置和部署組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 58397c35-6048-4ac9-a8b8-a528dd1cb82a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 867fe91ad0dd8dcb00c0293da08753f38e5005d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988271"
---
# <a name="lesson-4-building-and-deploying-the-assembly"></a>第 4 課： 建置和部署組件
在這一課，您可以建置並部署此專案以產生包含您在先前的課程中建立的結構描述的組件。 此工作可確保您到目前為止所建立的工作中沒有任何編譯錯誤。  
  
 部署組件會將組態資料庫中的組件的複本，並安裝到全域組件快取 (GAC) 中。 在下列程序中，您將部署直接從 [方案總管]。  
  
 當專案編譯成組件 （DLL 檔案），Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將儲存在 DLL \<*磁碟機*\>: \Program Files\\Microsoft BizTalk Accelerator for SWIFT\bin\在專案資料夾中的 [開發] 資料夾。  
  
### <a name="to-build-and-deploy-the-project"></a>建置和部署專案  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下**建置**。  
  
   > [!NOTE]
   >  確認**建置成功**會出現在畫面左下角。 在編譯過程中，您可能會看到一些狀態訊息。 SWIFT 結構描述在處理時，這些訊息是正常的。 如果出現任何錯誤，請按一下 工具，然後按一下 BizTalk Server 管理，以開啟 BizTalk Server 管理主控台。 在 BizTalk 管理主控台使用 「 事件檢視器 」 和健全狀況與活動追蹤 (HAT) 功能，若要更正錯誤並重建。  
  
2. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \labs\SWIFTProject\SWIFTSchemas\bin\Development**資料夾中，並確認**SWIFTSchemas.dll**檔案存在於這個資料夾中。  
  
3. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下**部署**。  
  
   > [!NOTE]
   >  確認**部署成功**會出現在畫面的左下角。  
  
### <a name="to-confirm-deployment-success"></a>若要確認部署成功  
  
1. 按一下 [**檢視**，然後按一下**BizTalk 總管] 中**。  
  
2. 依序展開**組件**節點，並確認**SWIFTSchemas (1.0.0.0)** 出現在清單中。  
  
    如果 SWIFTSchemas 出現在清單中，組件已成功部署和可參考，並使用從其他[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。  
  
   請繼續進行[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)。