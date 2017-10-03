---
title: "步驟 1： 建立及部署通用標頭和通知結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, headers
ms.assetid: e0f11f58-9a8c-4567-a537-3d182fa7dce2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a134071ee1973961e0fb4ed9b4da73ad87d8dbb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-and-deploy-common-header-and-acknowledgment-schemas"></a>步驟 1： 建立及部署通用標頭和通知結構描述
您可以使用標頭結構描述來驗證訊息執行個體的標頭 （MSH 區段）。 您可以使用通知結構描述來產生訊息執行個體的通知。 此程序適用於所有 HL7 結構描述版本。  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a>若要建立之標頭和通知結構描述  
  
1.  啟動**Microsoft Visual Studio 2012**。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
3.  在 [新增專案] 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
4.  在**範本**清單中，選取**btahl7v2xc 通用專案**。  
  
5.  在**名稱**欄位中，輸入**Interrogative_2XSchemas**，然後按一下 **確定**。  
  
     在方案總管 中，請注意，在專案中包含三個結構描述 （ACK_24_GLO_DEF.xsd、 ACK_25_GLO_DEF.xsd 和 MSH_25_GLO_DEF.xsd）。  
  
     保持開啟，Visual Studio。  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a>步驟 1A： 指派強式金鑰組件和部署  
 若要將組件的強式金鑰，然後再部署組件使用下列程序。  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>指派強式金鑰，並部署組件  
  
1.  啟動**Visual Studio 2012 的命令提示字元**。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元，將您的目錄變更\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\Interrogative 教學課程 資料夾。  
  
3.  在命令提示字元中，輸入**sn – k key.snk**，然後按下**Enter**。 請在 [輸出] 視窗中出現的成功訊息。  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的組件。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_2XSchemas**專案，然後再按一下**屬性**。  
  
5.  在 [Interrogative_2XSchemas 屬性頁] 對話方塊中，按一下**組件**。  
  
6.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。  
  
7.  在 組件金鑰檔案 對話方塊中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\Interrogative 教學課程中，按一下**key.snk**，然後按一下 **開啟**。  
  
8.  在 Interrogative_2XSchemas 屬性頁 對話方塊中，按一下**確定**以儲存變更。  
  
9. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_2XSchemas**專案，然後再按一下**部署**。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果未出現正確的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的部署。  
  
 若要繼續[步驟 2： 建立 V2.4 的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)。