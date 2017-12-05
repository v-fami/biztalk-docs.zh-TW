---
title: "管線範本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, templates
- Pipeline Designer, templates
- send pipelines, templates
- receive pipelines, templates
ms.assetid: b9779159-e49d-47fb-aa1c-06be5d604c67
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92cff5e945fad7716f31aa666731fe5d6a365146
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="pipeline-templates"></a>管線範本
除了預設管線，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 還包含兩個管線範本：接收管線範本和傳送管線範本。 從 BizTalk 專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您也可以使用您的專案新增管線範本**加入新項目**命令**專案**功能表。 各個範本都有相關聯的原則檔案，可決定管線的階段並指出管線中可以使用哪些管線元件。 您無法重新排序原則檔案中的階段，但您可以使用「管線設計師」來重新排序階段中的元件。  
  
 原則檔案可以指定：  
  
-   各階段的順序。  
  
-   各階段允許的元件數目。  
  
-   各階段的執行模式。  
  
 管線範本的原則檔案會儲存在 *\<BizTalk Server 安裝目錄\>*\Developer Tools\Pipeline 原則檔。 請勿修改原則檔案。 若要對管線進行變更，請開啟管線範本並使用「管線設計師」進行修改。 如需使用管線設計師 」 的詳細資訊，請參閱[使用管線設計師](../core/using-pipeline-designer.md)。  
  
 空白管線範本檔案會儲存在 *\<BizTalk Server 安裝目錄\>*\Developer Tools\BizTalkProjectItems，且名為 BTSReceivePipeline.btp 和 BTSTransmitPipeline.btp. 副檔名.btp 表示檔案是 BizTalk Server 管線可以在管線設計師中編輯。  
  
## <a name="see-also"></a>請參閱  
 [類型的管線](../core/types-of-pipelines.md)   
 [類型的管線元件](../core/types-of-pipeline-components.md)   
 [預設管線](../core/default-pipelines.md)   
 [管線元件](../core/pipeline-components.md)   
 [關於管線、階段和元件](../core/about-pipelines-stages-and-components.md)