---
title: 第 2 課： 加入專案參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- references [projects]
- projects, adding references
ms.assetid: ddc2bf49-cddd-4edb-8043-870897879655
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e7ade122e725c07772dba431bd364bc8f933b82
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969695"
---
# <a name="lesson-2-adding-project-references"></a>第 2 課： 加入專案參考
讓您的管線可以存取位於 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll 檔案中的預設執行階段結構描述，您就會加入專案參考。 此組件檔會包含標頭結構描述具有訊息類型解析所需的升級屬性。  
  
 您參考標頭結構描述稍後當您將反組譯碼元件新增至接收管線。  
  
### <a name="to-add-a-reference-to-the-default-swift-runtimeschemas-assembly"></a>若要加入預設 SWIFT RuntimeSchemas 組件的參考  
  
1.  在 [方案總管] 中，請確認**SWIFTPipelines**專案就會展開。 以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。  
  
2.  在 加入參考 對話方塊中，按一下**瀏覽** 索引標籤。  
  
3.  瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies**。  
  
4.  選取  **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll**檔案。  
  
5.  按一下 **新增**，然後按一下**確定**。  
  
    > [!NOTE]
    >  您現在已選取 RuntimeSchemas 組件 (dll) 會出現在 SWIFTPipelines 專案中參考集合。  
  
#### <a name="to-add-a-reference-to-the-swiftpipelines-schemas-assembly"></a>若要新增 SWIFTPipelines 結構描述組件的參考  
  
1. 在 方案總管底下**SWIFTPipelines**專案中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。  
  
2. 在 加入參考 對話方塊中上,**專案**索引標籤上，按一下**SWIFTSchemas**專案，按一下 **新增**，然後按一下  **確定**。  
  
3. 在上**檔案**功能表上，按一下**全部儲存**以儲存變更。  
  
   請繼續進行[第 3 課： 加入自訂接收管線](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)。