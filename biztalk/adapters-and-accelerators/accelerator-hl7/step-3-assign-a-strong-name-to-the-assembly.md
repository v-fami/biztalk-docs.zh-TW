---
title: 步驟 3： 指派強式名稱組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies
- message enrichment tutorial, strong name assemblies
- strong name assemblies
ms.assetid: 8709e4e1-b428-42af-ba3c-08225c17a9eb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57368dbbb2d8ecaa6621707ea7b989bf7f5b005d
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "26004951"
---
# <a name="step-3-assign-a-strong-name-to-the-assembly"></a>步驟 3： 指派強式名稱組件
在此步驟中，建立並指派強式名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]組件。 強式名稱組件提供數個安全性優點，才能部署您的專案在全域組件快取 (GAC) 中。 強式名稱可保證組件的唯一性，藉由指派數位簽章和唯一的索引鍵組合。 這也會保護方法是確保沒有人可以產生後續版本的組件的組件的歷程。 最後，強式名稱提供強式的完整性檢查，以保證組件的內容有不會變更建置它之後。  
  
### <a name="to-assign-a-strong-name-to-the-assembly"></a>若要指派強式名稱組件  
  
1.  啟動 **Visual Studio 命令提示字元**。  
  
    > [!NOTE]
    >  如果您已經建立強式名稱金鑰，您可以重複使用。  
  
2.  在命令提示字元中，移至**\<*磁碟機*\>: \Tutorial\BTAHL7V22Common** (其中\<*磁碟機*\>是安裝磁碟機代號），然後按**Enter**。  
  
3.  在命令提示字元中，輸入**sn – k key.snk**，然後按下**Enter**。 出現訊息指出，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]金鑰組寫入金鑰檔 key.snk。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V22Common**專案，然後再按一下**屬性**。  
  
5.  在 [BTAHL7V22Common 屬性頁] 對話方塊中，按一下**組件**。  
  
6.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。  
  
7.  在 組件金鑰檔案 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common\key.snk**，按一下 **開啟**，然後按一下**確定**。  
  
8.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下 **部署**。 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]建立您可以從下一個專案參考的組件。  
  
9. Btahl7v2xc 通用專案重複步驟 4 到 8。  
  
 若要繼續[步驟 4： 建立結構描述](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)