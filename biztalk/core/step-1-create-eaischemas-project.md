---
title: 步驟 1： 建立 EAISchemas 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a14ee61-fa27-4f03-997e-42c34a77afee
caps.latest.revision: 55
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb51c936edfcc20009048abcb90bb8ead72fd11c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974455"
---
# <a name="step-1-create-eaischemas-project"></a>步驟 1：建立 EAISchemas 專案
![步驟 1，共 5](../core/media/step-1of5.gif "Step_1of5")  

 **若要完成的時間：** 5 分鐘  

 **目標：** 在此步驟中，您建立新[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案和專案。  

 **用途：** 您可以使用 BizTalk 專案系統以建立部分或所有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]應用程式或商務方案。 任何這類方案的核心項目為 BizTalk 專案—為部署之前建置和產生至組件的結構描述、協調流程、Web 訊息類型、類別、管線、對應和參考等項目的集合。  

## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  

-   在開始此步驟之前，您就必須完成中的步驟[在您開始本教學課程之前](../core/before-you-begin-the-tutorial.md)。  

## <a name="procedures"></a>程序  

#### <a name="to-create-a-new-visual-studio-solutionproject"></a>若要建立新的 Visual Studio 方案/專案  

1. 開始**Microsoft Visual Studio**。  

2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  

3. 在 **新的專案**對話方塊方塊中，執行下列動作：  


   |             使用              |                                以進行此動作                                |
   |-----------------------------------|--------------------------------------------------------------------------|
   |      **已安裝的範本**      | 按一下  **BizTalk 專案**，然後按一下**空白 BizTalk Server 專案**。 |
   |             **名稱**              |                           型別**EAISchemas**。                           |
   |           **位置**            |                      型別**C:\tutorial\Lessons**。                       |
   |         **方案名稱**         |                          型別**EAISolution**。                           |
   | **為解決方案建立目錄** |                                (已選取)                                |


4. 按一下 [確定] 。  

5. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  

## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中開啟了新專案和 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 方案。  

## <a name="next-steps"></a>後續步驟  
 您會建立庫存補充要求訊息的結構描述。  

## <a name="see-also"></a>另請參閱  
 [開始本教學課程之前](../core/before-you-begin-the-tutorial.md)   
 [步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)   
 [步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md)   
 [步驟 4： 建立對應](../core/step-4-create-the-map.md)   
 [步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md)   
 [開發人員工具](../core/developer-tools.md)   
 [使用 BizTalk 專案](../core/working-with-biztalk-projects.md)