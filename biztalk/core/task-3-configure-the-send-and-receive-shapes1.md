---
title: 工作 3： 設定傳送埠和接收 Shapes1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e258d22-755b-48a4-9f9e-e9398f6b68b1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c730cc6bc5cb11c27152613f331bda6b15be390
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278814"
---
# <a name="task-3-configure-the-send-and-receive-shapes"></a>工作 3： 設定傳送埠和接收圖形
請使用下列程序設定傳送和接收圖形。  
  
### <a name="to-configure-the-send-and-receive-shapes"></a>若要設定傳送和接收圖形  
  
1.  依照下列順序，將傳送和接收圖形從工具箱中拖到協調流程的中央位置。  
  
2.  設定下列參數：  
  
    |形狀圖|名稱|設定|  
    |-----------|----------|-------------|  
    |Receive1|Activate|True|  
    ||訊息|BeginDocMsg|  
    ||名稱|ReceiveBeginDoc|  
    ||作業|BeginDoc.Operation_1.Request|  
    |Send1|訊息|BeginDocSessionMsg|  
    ||名稱|SendBeginDoc|  
    ||作業|JDEPort.Operation_1.Request|  
    |Receive2|Activate|False|  
    ||訊息|BeginDocResponseMsg|  
    ||名稱|ReceiveBeginDocResponse|  
    ||作業|JDEPort.Operation_1.Response|  
    |Send2|訊息|EditLineSessionMsg|  
    ||名稱|SendEditLine|  
    ||作業|JDEPort.Operation_2.Request|  
    |Receive3|Activate|False|  
    ||訊息|EditLineResponseMsg|  
    ||名稱|ReceiveEditLine|  
    ||作業|JDEPort.Operation_2.Response|  
    |Send3|訊息|EndDocSessionMsg|  
    ||名稱|SendEndDoc|  
    ||作業|JDEPort.Operation_3.Request|  
    |Receive4|Activate|False|  
    ||訊息|EndDocResponseMsg|  
    ||名稱|ReceiveEndDocResponse|  
    ||作業|JDEPort.Operation_3.Response|  
    |Send4|訊息|EndDocResponseMsg|  
    ||名稱|SendEndDocResponse|  
    ||作業|EndDocOut.Operation_1.Request|  
  
## <a name="see-also"></a>另請參閱  
 [工作 1： 建立連接埠](../core/task-1-create-the-ports2.md)   
 [工作 2： 建立訊息](../core/task-2-create-the-messages1.md)   
 [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape2.md)   
 [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape1.md)