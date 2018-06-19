---
title: 第 4 課： 建立和部署組件 |Microsoft 文件
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
ms.openlocfilehash: 3ca5a539fdaea9026a7c18cae6f076e72df9efe2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25961924"
---
# <a name="lesson-4-building-and-deploying-the-assembly"></a>第 4 課： 建立和部署組件
在這一課，您會建置並部署此專案以產生包含您在先前的課程中建立的結構描述的組件。 這項工作可確保您到目前為止所建立的工作中沒有編譯錯誤。  
  
 部署組件的組件的複本置於組態資料庫，並將它安裝在全域組件快取 (GAC) 中。 在下列程序中，您將部署直接從 [方案總管]。  
  
 當專案編譯成組件 （DLL 檔案）， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將儲存在 DLL \<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator forSWIFT\bin\Development 資料夾在專案資料夾中。  
  
### <a name="to-build-and-deploy-the-project"></a>建置和部署專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下 **建置**。  
  
    > [!NOTE]
    >  確認**建置成功**會出現在畫面左下角。 在編譯過程中，您可能會看到某些狀態訊息。 這些訊息都是正常的處理 SWIFT 的結構描述時。 如果出現任何錯誤，請按一下 工具，然後按一下 BizTalk Server 管理 以開啟 BizTalk Server 管理主控台。 使用事件檢視器和健全狀況與活動追蹤 (HAT) 中的功能 BizTalk 管理主控台來更正錯誤，然後再重建。  
  
2.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \labs\SWIFTProject\SWIFTSchemas\bin\Development**資料夾，並確認**SWIFTSchemas.dll**檔案位於此資料夾。  
  
3.  在 方案總管 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下 **部署**。  
  
    > [!NOTE]
    >  確認**部署成功**會出現在畫面左下角。  
  
### <a name="to-confirm-deployment-success"></a>若要確認部署成功  
  
1.  按一下**檢視**，然後按一下  **BizTalk 總管**。  
  
2.  展開**組件**節點，並確認**SWIFTSchemas (1.0.0.0)** 出現在清單中。  
  
     如果 SWIFTSchemas 出現在清單中，組件已成功部署和可參考，並使用從其他[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。  
  
 若要繼續[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)。