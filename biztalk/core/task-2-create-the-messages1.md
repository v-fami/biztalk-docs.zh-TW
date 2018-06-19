---
title: 工作 2： 建立 Messages1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df908ea0-b3be-47e6-99ba-4122cb1db561
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e326662737919e325f95d82b86aa8824e4e3a06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278846"
---
# <a name="task-2-create-the-messages"></a>工作 2： 建立訊息
建立下列訊息，這些訊息將在協調流程中使用。  
  
### <a name="to-create-the-messages"></a>建立訊息  
  
1.  以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。  
  
2.  針對 [識別項] 和 [訊息類型] > [結構描述] 填入下列內容，並且從各訊息顯示的清單中選取類型。  
  
    |識別碼|訊息類型 > 結構描述|  
    |----------------|--------------------------|  
    |BeginDocMsg|BeginDocTest.B4200310Service_1.F4211FSBeginDoc|  
    |BeginDocResponseMsg|BeginDocTest.B4200310Service_1.F4211FSBeginDocResponse|  
    |BeginDocSessionMsg|BeginDocTest.B4200310Service_1.F4211FSBeginDoc|  
    |EditLineMsg|BeginDocTest.B4200310Service_1.F4211FSEditLine|  
    |EditLineResponseMsg|BeginDocTest.B4200310Service_1.F4211FSEditLineResponse|  
    |EditLineSessionMsg|BeginDocTest.B4200310Service_1.F4211FSEditLine|  
    |EndDocMsg|BeginDocTest.B4200310Service_1.F4211FSEndDoc|  
    |EndDocResponseMsg|BeginDocTest.B4200310Service_1.F4211FSEndDocResponse|  
    |EndDocSessionMsg|BeginDocTest.B4200310Service_1.F4211FSEndDoc|  
  
## <a name="see-also"></a>另請參閱  
 [工作 1： 建立連接埠](../core/task-1-create-the-ports2.md)   
 [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md)   
 [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape2.md)   
 [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape1.md)