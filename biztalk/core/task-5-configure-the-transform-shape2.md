---
title: 工作 5： 設定轉換 Shape2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e92874e-9021-4cf6-bab6-d4173308c469
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39ccfdff1f175942dfc5b3ce5c6ba75c87dcf2de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000159"
---
# <a name="task-5-configure-the-transform-shape"></a>工作 5： 設定轉換圖形
請使用下列程序設定「轉換」圖形。  
  
### <a name="to-configure-the-transform-shape"></a>設定轉換圖形  
  
1. 將「建構訊息」圖形拖曳至 ReceiveBeginDocResponse 後面。  
  
   -   **建構的訊息：** EditLineMsg  
  
   -   **名稱：** ConstructEditLineMessageWithData  
  
   1. 以滑鼠右鍵按一下中央，選取**插入圖形**，然後選取**轉換**。  
  
       ![插入圖形轉換](../core/media/insert-shape-transform.gif "insert_shape_transform")  
  
   2. 使用 [轉換]，對應來自您要傳送至已傳送資料的資料。  
  
      針對您的工作環境，您可能會傳送文件 (而非 BeginDoc)，其中包含可讓您建構所有可能訊息、BeginDoc、EditLine 和 EndDoc 的所有值。 不過，此範例只有硬式編碼資料。  
  
2. 按兩下 [Transform_1] 將它開啟。  
  
   1.  選取來源，在底下的 加入資料列中按一下**變數名稱**，然後選取**begindocresponsemsg**。  
  
        ![將來源轉換](../core/media/transform-source.gif "transform_source")  
  
   2.  選取**目的地**下方的 加入資料列中按一下 **變數名稱**，選取**EditLineMsg**，然後按一下**確定**。  
  
        ![轉換目的](../core/media/transform-destination.gif "transform_destination")  
  
3. 在 [方案總管] 中，按兩下 **[transform_1.btm]** 以開啟對應工具。 連結下列四個項目：  
  
   - mnCMJobNo  
  
   - szCMComputerID  
  
   - mnProcessID  
  
   - mnTransactionID  
  
     ![範例轉換對應](../core/media/example-transformmapping.gif "example_transformmapping")  
  
     為了方便使用起見，此範例包含硬式編碼值。 按一下 [目的結構描述] 中的項目，並設定下列值。  
  
     ![硬式編碼的對應](../core/media/hardcoded-mapping-example.gif "hardcoded_mapping_example")  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:F4211FSEditLine xmlns:ns0="http://schemas.microsoft.com/  
         [JDE://CSALES/B4200310]">  
      <ns0:cCMLineAction>A</ns0:cCMLineAction>  
      <ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
      <ns0:cCMWriteToWFFlag>2</ns0:cCMWriteToWFFlag>  
      <ns0:szItemNo>210</ns0:szItemNo>  
      <ns0:mnQtyOrdered>1</ns0:mnQtyOrdered>  
      <ns0:cSalesTaxableYN>N</ns0:cSalesTaxableYN>  
      <ns0:szTransactionUOM>EA</ns0:szTransactionUOM>  
      <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
      <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
   </ns0:F4211FSEditLine>  
   ```  
  
4. 將「建構訊息」拖曳至 ReceiveEditLine 後面。  
  
   -   **建構的訊息：** EndDocMsg  
  
   -   **名稱：** ConstructEndDocMessageWithData  
  
        以滑鼠右鍵按一下中央並選取**插入圖形**，然後選取**轉換**。  
  
5. 按兩下 [Transform_2] 將它開啟。  
  
   1.  選取 **來源**下方的 加入資料列中按一下 **變數名稱**，然後選取**begindocresponsemsg**。  
  
   2.  選取**目的地**下方的 加入資料列中按一下 **變數名稱**，選取**EndDocMsg**，然後按一下**確定**。  
  
6. 在 [方案總管] 中，按兩下 **[transform_2.btm]** 以開啟對應工具。 連結下列四個項目：  
  
   - mnCMJobNo  
  
   - szCMComputerID  
  
   - mnProcessID  
  
   - mnTransactionID  
  
     為了方便使用起見，此範例包含硬式編碼值。 按一下 [目的結構描述] 中的項目，並設定下列值。  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
       [JDE://CSALES/B4200310]">  
      <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
      <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
      <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
   </ns0:F4211FSEndDoc>  
   ```  
  
## <a name="see-also"></a>另請參閱  
 [工作 1： 建立連接埠](../core/task-1-create-the-ports1.md)   
 [工作 2： 建立訊息](../core/task-2-create-the-messages2.md)   
 [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes2.md)   
 [工作 4：設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape1.md)