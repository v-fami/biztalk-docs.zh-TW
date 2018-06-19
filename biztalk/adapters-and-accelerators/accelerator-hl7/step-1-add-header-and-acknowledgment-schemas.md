---
title: 步驟 1： 加入標頭和通知結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 808132bf-02e7-4ff4-b914-9fae5d27e5fd
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f79778801b1ca70d4e8356a24886c792fe447e33
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005335"
---
# <a name="step-1-add-header-and-acknowledgment-schemas"></a>步驟 1： 加入標頭和通知結構描述
在此步驟中，您可以建立新 BTAHL72XCommon 專案範本為基礎的專案。 此範本包含三種常見的結構描述，訊息標頭 (MSH_25_GLO_DEF.xsd) 和通知 (ACK_24_GLO_DEF.xsd) 和 (ACK_25_GLO_DEF.xsd)。 您必須包含在專案中這些結構描述，該 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 組建及/或正確驗證的訊息標頭和通知。 此程序之間是共通的所有結構描述版本[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.X。  
  
 您也建立強式金鑰、 將它指派給組件，然後再部署組件。 強式金鑰組件提供安全性和身分識別，而且不需要進行部署。 當您部署組件時，它會儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫） 和全域組件快取 (GAC) 中。  
  
### <a name="to-create-the-project-and-add-header-and-acknowledgment-schemas"></a>若要建立專案並加入標頭和通知結構描述  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在 新增專案 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後按一下  **BTAHL7Projects**。  
  
3.  在**範本**清單中，按一下**btahl7v2xc 通用專案**。  
  
4.  在**名稱**方塊中，輸入**btahl7v2xc 通用**做為專案名稱。  
  
5.  在**位置**方塊中，瀏覽至 **\<** *磁碟機***:\>\Batching 教學課程**。  
  
6.  按一下 **[確定]**。  
  
> [!NOTE]
>  在方案總管 中，三個結構描述 （MSH_25_GLO_DEF.xsd、 ACK_24_GLO_DEF.xsd 和 ACK_25_GLO_DEF.xsd） 都包含在專案中。  
  
### <a name="to-assign-a-strong-key-to-the-assembly-and-deploy"></a>若要指派至組件的強式金鑰，部署  
  
1.  開啟**Visual Studio 命令提示字元**。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元中，瀏覽至 **\<** *磁碟機***\>: \Batching 教學課程**資料夾。  
  
3.  在命令提示字元中，輸入**sn – k key.snk**，然後按 ENTER 鍵。 請在 [輸出] 視窗中出現的成功訊息。  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的組件。  
  
4.  在 方案總管 中，以滑鼠右鍵按一下**btahl7v2xc 通用專案**，然後按一下 **屬性**。  
  
5.  在**btahl7v2xc 通用專案屬性頁**對話方塊中，按一下 **簽署**。  
  
6.  請檢查**簽署組件**核取方塊。  
  
7.  在**選擇強式名稱**金鑰檔 下拉式清單中，選取**\<瀏覽...\>**.  
  
8.  瀏覽至\<*磁碟機*\>: \Batching 教學課程中，選取**key.snk**，然後按一下 **開啟**。  
  
9. 在 btahl7v2xc 通用專案屬性頁 視窗中，按一下**確定**以儲存變更。  
  
10. 在 方案總管 中，以滑鼠右鍵按一下**btahl7v2xc 通用專案**，然後按一下 **部署**。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果未出現正確的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的部署。  
  
 若要繼續[步驟 2： 加入常見的結構描述的 v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md)。