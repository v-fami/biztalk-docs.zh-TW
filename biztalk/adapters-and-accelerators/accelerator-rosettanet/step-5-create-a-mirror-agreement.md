---
title: 步驟 5： 建立鏡像協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, mirror agreements
- loopback tutorial, creating mirror agreements
- agreements, mirror agreements
ms.assetid: 6aa70b1e-7d38-49f7-9d5f-f008cbe3df66
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fde79b9ee5cdbb5cd34440aa59e79e842f79b0b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006463"
---
# <a name="step-5-create-a-mirror-agreement"></a>步驟 5： 建立鏡像協議
在此步驟中，您將使用回送公用程式，在設定主要組織的相同電腦上，建立模擬交易夥伴的鏡像協議。 回送公用程式是命令列工具。  
  
### <a name="to-create-a-mirror-agreement-using-the-loopback-utility"></a>使用回送公用程式建立鏡像協議  
  
1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，移至\<*磁碟機*\>: \Program 檔案 (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK。 輸入下列命令，然後按**Enter**:  
  
   ```  
   Loopback /enable HOME  
   ```  
  
3. 步驟 2 中執行的命令完成之後，在命令提示字元中，輸入下列命令，然後按**Enter**:  
  
   ```  
   Loopback /mirror "Trade Agreement"   
   ```  
  
   回送公用程式會自動為主要組織 (啟動者) 建立傳送埠，並為交易夥伴組織建立鏡像交易協議。 交易夥伴將使用這兩個新的傳送埠與主要組織通訊。  
  
> [!NOTE]
>  每當您更新原始交易協議，就必須重新建立鏡像交易協議。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 6：啟動協調流程](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)
