---
title: "步驟 7： 簽署和建置的專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, projects
- projects, building
- projects, signing
ms.assetid: b66e4dc1-4ec6-4ec0-a69a-419b116b19c1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70f77e536da4eb6589823529644e0c4ab7c95cfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-sign-and-build-the-projects"></a>步驟 7： 簽署和建置的專案
在此步驟中，您指派強式名稱，並建置專案來產生組件，其中包含您在中建立的資源 （結構描述）[步驟 6： 驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)。 這也可確保您到目前為止完成的工作中沒有編譯錯誤。  
  
### <a name="to-sign-the-btahl7-project"></a>BTAHL7 專案簽章  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**屬性**。  
  
2.  在 [BTAHL7 專案屬性頁] 對話方塊中，按一下**組件**。  
  
3.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。  
  
4.  在 [組件金鑰檔案] 對話方塊中，瀏覽至  **\<*磁碟機*>: \Tutorial\BTAHL7V22Common\key.snk** (在中建立[步驟 3： 指派強式名稱組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md))，然後按一下**開啟**。  
  
5.  按一下**確定**以儲存變更。  
  
### <a name="to-build-the-btahl7-project"></a>若要建置 BTAHL7 專案  
  
-   在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**部署**。 [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]會編譯成 DLL 檔案的組件，並將儲存在\<*磁碟機*>: \Tutorial\BTAHL7V22Common\Bin\Development 資料夾。  
  
 若要繼續[步驟 8： 使用 BizTalk 對應工具建立對應](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)