---
title: 步驟 1： 建立及部署標頭和通知結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, header schemas
- header schemas
ms.assetid: 3ff013a4-6c67-4bac-be97-81b2dc5b6119
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9ffa8ab8d80a8b2da172378349eb9761a728fb7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960740"
---
# <a name="step-1-create-and-deploy-header-and-acknowledgment-schemas"></a>步驟 1： 建立及部署標頭和通知結構描述
您可以使用標頭結構描述來驗證訊息執行個體的標頭 （MSH 區段）。 您可以使用通知結構描述來產生訊息執行個體的通知。 此程序之間是共通的所有結構描述版本[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.X。  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a>若要建立之標頭和通知結構描述  
  
1.  啟動**Microsoft Visual Studio 2012**。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
3.  在 [新增專案] 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
4.  在 範本 區段中，選取**btahl7v2xc 通用專案**，然後按一下 **確定**。  
  
     在方案總管 中，請注意，在專案中包含三個結構描述 （ACK_24_GLO_DEF.xsd ACK_25_GLO_DEF.xsd 和 MSH_25_GLO_DEF.xsd）。  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a>步驟 1A： 指派強式金鑰組件和部署  
 若要將組件的強式金鑰，然後再部署組件使用下列程序。  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>指派強式金鑰，並部署組件  
  
1.  啟動**Visual Studio 2012 的命令提示字元**。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元中，瀏覽至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for HL7 \SDK\端對端教學課程的資料夾。  
  
3.  在命令提示字元中，輸入**sn – k key.snk**，然後按 ENTER 鍵。 請確定下列成功訊息出現在 輸出 視窗，然後關閉 命令視窗。  
  
     **「 金鑰組寫入 key.snk。 」**  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的組件。  
  
4.  在 方案總管 中，以滑鼠右鍵按一下**btahl7v2xc 通用 Project1**，然後按一下 **屬性**。  
  
5.  在 btahl7v2xc 通用 Project1 屬性頁] 頁面上，按一下 [**組件**。  
  
6.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 (**...**) 按鈕。  
  
7.  在 [組件金鑰檔案] 對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程，請選取**key.snk**，然後按一下**開啟**。  
  
8.  Btahl7v2xc 通用專案屬性] 頁面上，按一下 [**確定**以儲存變更。  
  
9. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在**方案總管] 中**，以滑鼠右鍵按一下**btahl7v2xc 通用專案**，然後按一下 [**部署**。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果未出現正確的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的部署。  
  
 若要繼續[步驟 2： 建立 V2.3.1 的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)。