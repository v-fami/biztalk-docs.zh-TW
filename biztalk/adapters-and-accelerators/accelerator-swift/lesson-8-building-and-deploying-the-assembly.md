---
title: 第 8 課： 建置和部署組件 |Microsoft Docs
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
ms.assetid: 74c9dfbd-8365-4600-8885-a9d9c3490dd5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80e97076bb503d51bd2180c3f4bea950c0c04a46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968383"
---
# <a name="lesson-8-building-and-deploying-the-assembly"></a>第 8 課： 建置和部署組件
在這一課，您可以建置和部署管線專案以產生包含您在上一個步驟中建立管線的組件。 這一課中，可確保您到目前為止已建立的工作中沒有任何編譯錯誤。  
  
 您將專案編譯到組件 (DLL) 檔案，並將它儲存在\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\bin\Development 資料夾。  
  
### <a name="to-build-and-deploy-the-project"></a>建置和部署專案  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTPipelines**，然後按一下**建置**。  
  
   > [!NOTE]
   >  在編譯過程中，您應該不會看到任何失敗。 如果這麼做，請檢查錯誤的來源更正它，然後重新建置專案。 不過，您可能會看到 A4SWIFT 管線元件相關的警告數目。 您可以更正設定導致這些警告的狀況**複製到本機**屬性的管線元件參考加入至**False**。 如需詳細資訊，請參閱 「 建置管線專案可能會導致警告 」，在[其他已知問題](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6)。  
  
2. 若要確認是否已建立 SWIFTPipelines.dll 檔案、 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*:\>\labs\SWIFTProject\SWIFTPipelines\bin\Development，並確定該檔案位於此資料夾中。  
  
3. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTPipelines**，然後按一下**部署**。  
  
   > [!NOTE]
   >  在部署過程中，您應該不會看到任何錯誤或警告。 如果您這樣做，請檢查錯誤的來源、 更正它，和重新部署專案。  
  
4. 在符合部署成功**檢視**功能表[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 [ **BizTalk 總管] 中**。  
  
5. 以滑鼠右鍵按一下**BizTalk 組態資料庫**，然後按一下**重新整理**。  
  
6. 依序展開**組件**節點，並確認加速器是否成功部署**SWIFTPipelines (1.0.0.0)**。  
  
   請繼續進行[模組 4： 建立 XML 接收和一般檔案傳送埠](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)。