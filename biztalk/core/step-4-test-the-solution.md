---
title: "步驟 4： 測試方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c39521-eee2-49f7-a9f9-2dfb9ab468e9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f0ae6cb124ea9d8710797790b9176289faafc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-solution"></a>步驟 4： 測試方案
本主題，您會測試方案，藉由在您與檔案相關聯的資料夾中放置虛擬要求訊息在接收埠。 中所述，而叫用虛擬要求訊息置放**Wcf-webhttp**傳送埠。 您可以建立虛擬要求訊息，如下所示：  
  
```  
<Root>  
  <Input>Azure Market Place REST API integration</Input>  
<Root>  
```  
  
### <a name="to-test-the-solution"></a>測試方案  
  
1.  從 BizTalk Server 管理主控台，啟動**BizTalk Application 1**。 這樣會啟動在先前步驟中建立的所有連接埠。  
  
2.  開啟 Windows 檔案總管並瀏覽至您與檔案相關聯的位置接收位置。 在這個位置，複製虛擬要求訊息。  
  
3.  當檔案消失時，請檢查您與使用 REST 介面的回應訊息的 FILE 傳送埠相關聯的位置。 它應該包含的 XML 回應訊息。 開啟該 XML 訊息，以查看從美國空中會延遲班機的詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 5： 叫用 REST 介面使用 BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)