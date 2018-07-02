---
title: 傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58ca6a63-525a-4b16-932d-6d26e68f6fab
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5700b3adb0769edff4ec820b4d95353383c08e6d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968015"
---
# <a name="send-pipeline"></a>傳送管線
此範例提供了有效 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]傳送管線，您可以自訂您的應用程式。  
  
## <a name="demonstrates"></a>示範  
 這個範例示範如何使用 BTARN 傳送管線 (PipelineSend.btp)，將 XML 訊息外送至對等的 RNIF 訊息中。 PipelineSend.btp 位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\rnpipelines。 它包含下列階段：  
  
-   XML 組合器  
  
-   MIME 編碼器  
  
-   傳送不可否認的訊息  
  
> [!NOTE]
>  如果您在 Visual Studio 的「管線設計師」中選取 BTARN 傳送管線的上述其中一個元件，該元件的屬性將不會顯示在 [屬性] 窗格中。 若要顯示元件的屬性，您必須將元件加入 工具箱 中使用**選擇工具箱項目**工具 功能表中的命令; 刪除現有的元件從傳送管線，然後再新增從元件工具箱拖曳到 管線設計師 」 中的適當階段。 然後如果您再選取該元件，它的屬性就會顯示在 [屬性] 窗格中。  
  
 此管線中，以及此管線內的訊息流程元件的相關資訊，請參閱[BTARN 傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管線範例](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md)   
 [BTARN 傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)