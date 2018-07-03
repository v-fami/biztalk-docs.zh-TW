---
title: 第 2 課： 建立 SWIFTSchemas 專案的強式名稱 BizTalk 組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies, creating strong-names
- strong-named assemblies
ms.assetid: 2aacbf38-8b1d-46ea-89ae-5207327bedc1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8e5b9ccc56b6b75ea574f956faac462e5b35dca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995519"
---
# <a name="lesson-2-creating-a-strong-named-biztalk-assembly-for-the-swiftschemas-project"></a>第 2 課： 建立 SWIFTSchemas 專案的強式名稱 BizTalk 組件
在這一課，您會建立強式名稱的編譯和部署 BizTalk 組件。 強式名稱組件提供數個安全性優點：  
  
- 強式名稱可保證唯一性的組件，藉由指派數位簽章和唯一的金鑰組。  
  
- 強式名稱可保護組件的歷程，藉由確定沒有其他人可以產生組件的後續版本。  
  
- 強式名稱提供強式整體性檢查，以保證組件的內容，在上次建置以來尚未變更。  
  
  您可以產生金鑰檔使用強式名稱工具 (sn.exe) 隨附[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]或[!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)]。  
  
### <a name="to-create-a-strong-named-biztalk-assembly"></a>若要建立強式名稱 BizTalk 組件  
  
1. 啟動 Visual Studio 命令提示字元。  
  
2. 在 Visual Studio 命令提示字元中，瀏覽至\<*磁碟機*\>: \labs 資料夾。  
  
3. 在命令提示字元中，輸入**sn – k swift.snk**，然後按 ENTER 鍵。 請確定在 [輸出] 視窗中出現的成功訊息。  
  
   > [!NOTE]
   >  如果未出現正確的訊息，請使用 Visual Studio 來疑難排解您的組件。  
  
4. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**專案，然後再按一下**屬性**。  
  
5. 在 [SWIFTSchemas 屬性頁] 對話方塊中，確定**通用屬性**會展開，然後選取**組件**。  
  
6. 向下和右窗格中的組件屬性捲動**強式名稱**區段中，按一下右邊的方塊**組件金鑰檔案**。 按一下省略符號按鈕。  
  
7. 在 [組件金鑰檔案] 對話方塊中，瀏覽至 **\<*磁碟機*:\>\labs**。  
  
8. 選取  **swift.snk**金鑰的檔案，為檔案，然後按一下**開啟**。  
  
9. 在 [SWIFTSchemas 屬性頁] 對話方塊中，按一下**確定**。  
  
10. 在上**檔案**功能表上，按一下**全部儲存**以儲存變更。  
  
    請繼續進行[第 3 課： 將 SWIFT 結構描述加入至專案](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md)。