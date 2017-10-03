---
title: "工作 5： 設定轉換 Shape1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a73fd2-0f34-4681-8aed-7d54d69c86d3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e76313ca87ad3138da83480b46a38a802d89ff15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="task-5-configure-the-transform-shape"></a>工作 5： 設定轉換圖形
請使用下列程序設定「轉換」圖形。  
  
### <a name="to-configure-the-transform-shape"></a>設定轉換圖形  
  
1.  將「建構訊息」圖形拖曳至 ReceiveBeginDocResponse 後面。  
  
    -   **建構的訊息：** EditLineMsg  
  
    -   **名稱：** ConstructEditLineMessageWithData  
  
     以滑鼠右鍵按一下中央，選取**插入圖形**，然後選取**轉換**。  
  
     ![](../core/media/jde-insert-shape-transform.gif "JDE_insert_shape_transform")  
  
     使用 [轉換]，對應來自您要傳送至已傳送資料的資料。  
  
     針對您的工作環境，您可能會傳送文件 (而非 BeginDoc)，其中包含可讓您建構所有可能訊息、BeginDoc、EditLine 和 EndDoc 的所有值。 不過，此範例只有硬式編碼資料。  
  
2.  按兩下**[transform_1]**開啟。  
  
    1.  選取來源，在 加入資料列中按一下**變數名稱**選取**begindocresponsemsg**。  
  
         ![](../core/media/jde-transform-source.gif "JDE_transform_source")  
  
    2.  選取**目的地**按一下底下的 加入資料列中的 **變數名稱**，選取**EditLineMsg**，按一下**確定**。  
  
         ![](../core/media/jde-transform-destination.gif "JDE_transform_destination")  
  
3.  在 [方案總管] 中，按兩下**[transform_1.btm]**開啟對應工具。 連結下列四個項目：  
  
    -   mnCMJobNo  
  
    -   szCMComputerID  
  
    -   mnProcessID  
  
    -   mnTransactionID  
  
     ![](../core/media/jde-example-transformmapping.gif "JDE_example_transformmapping")  
  
     為了方便使用起見，此範例包含硬式編碼值。 按一下 [目的結構描述] 中的項目，並設定下列值。  
  
     ![](../core/media/jde-hardcoded-mapping-example.gif "JDE_hardcoded_mapping_example")  
  
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
  
4.  將「建構訊息」拖曳至 ReceiveEditLine 後面。  
  
    -   **建構的訊息：** EndDocMsg  
  
    -   **名稱：** ConstructEndDocMessageWithData  
  
     以滑鼠右鍵按一下中央並選取**插入圖形**，然後選取**轉換**。  
  
5.  按兩下**[transform_2]**開啟。  
  
    1.  選取**來源**按一下底下的 加入資料列中的 **變數名稱**選取**begindocresponsemsg**。  
  
    2.  選取**目的地**按一下底下的 加入資料列中的 **變數名稱**，選取**EndDocMsg**，按一下**確定**。  
  
6.  在 [方案總管] 中，按兩下**[transform_2.btm]**開啟對應工具。 連結下列四個項目：  
  
    -   mnCMJobNo  
  
    -   szCMComputerID  
  
    -   mnProcessID  
  
    -   mnTransactionID  
  
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
 [工作 1： 建立連接埠](../core/task-1-create-the-ports2.md)   
 [工作 2： 建立訊息](../core/task-2-create-the-messages1.md)   
 [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md)   
 [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape2.md)