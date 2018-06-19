---
title: 步驟 2： 建立 V2.4 通用結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, common schemas
ms.assetid: 333ae85a-a307-4ab1-97f4-4d7b986e91de
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60b199bcd350a3341640baa05b875347c4f04bb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960708"
---
# <a name="step-2-create-common-schemas-for-v24"></a>步驟 2： 建立 V2.4 通用結構描述
V2.4 結構描述是經常參考的結構描述，以用來驗證查詢和回應訊息執行個體。  
  
### <a name="to-create-the-common-schemas-for-v24"></a>若要建立 V2.4 常見的結構描述  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在 [新增專案] 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
3.  在**範本**清單中，選取**BTAHL7V24Common 專案**。  
  
4.  在**名稱**欄位中，輸入**Interrogative_24Schemas**。  
  
5.  在 方案 欄位中，選取**將加入至方案**，然後按一下 **確定**。  
  
     在方案總管 中，請注意，在專案中包含三個結構描述 （datatypes_24.xsd、 segments_24.xsd 和 tablevalues_24.xsd）。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_24Schemas**專案，然後再按一下**屬性**。  
  
7.  在 [Interrogative_24Schemas 屬性頁] 對話方塊中，按一下**組件**。  
  
8.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。  
  
9. 在**組件金鑰檔案**對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative 教學課程，按一下**key.snk**，然後按一下 **開啟**。  
  
10. 在 Interrogative_24Schemas 屬性頁 對話方塊中，按一下**確定**以儲存變更。  
  
11. 在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_24Schemas**專案，然後再按一下**部署**。 按一下**確定**對話方塊要求您將變更儲存到方案。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
 若要繼續[步驟 3： 建立和部署觸發程序事件 （訊息） 專案](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)。