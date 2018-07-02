---
title: 管線範本 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, templates
- Pipeline Designer, templates
- send pipelines, templates
- receive pipelines, templates
ms.assetid: b9779159-e49d-47fb-aa1c-06be5d604c67
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8075611bbf1f64de7b69ee92e1078dc5046c5de4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984983"
---
# <a name="pipeline-templates"></a>管線範本
除了預設管線，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 還包含兩個管線範本：接收管線範本和傳送管線範本。 從 BizTalk 專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以新增管線範本至您的專案使用**加入新項目**命令**專案**功能表。 各個範本都有相關聯的原則檔案，可決定管線的階段並指出管線中可以使用哪些管線元件。 您無法重新排序原則檔案中的階段，但您可以使用「管線設計師」來重新排序階段中的元件。  
  
 原則檔案可以指定：  
  
- 各階段的順序。  
  
- 各階段允許的元件數目。  
  
- 各階段的執行模式。  
  
  管線範本的原則檔案會儲存在 *\<BizTalk Server 安裝目錄\>* \Developer Tools\Pipeline 原則檔。 請勿修改原則檔案。 若要對管線進行變更，請開啟管線範本並使用「管線設計師」進行修改。 如需使用管線設計師的詳細資訊，請參閱[使用管線設計師](../core/using-pipeline-designer.md)。  
  
  空白管線範本檔案會儲存在 *\<BizTalk Server 安裝目錄\>* \Developer Tools\BizTalkProjectItems，且名為 BTSReceivePipeline.btp 和 BTSTransmitPipeline.btp. 檔案名稱副檔名.btp 表示檔案是 BizTalk Server 管線，並且可以在管線設計師中編輯。  
  
## <a name="see-also"></a>另請參閱  
 [管線類型](../core/types-of-pipelines.md)   
 [管線元件類型](../core/types-of-pipeline-components.md)   
 [預設管線](../core/default-pipelines.md)   
 [管線元件](../core/pipeline-components.md)   
 [關於管線、階段和元件](../core/about-pipelines-stages-and-components.md)