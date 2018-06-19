---
title: 工作 1： 建立 Ports1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b944a03-c8e2-4eba-9e11-10c14f929499
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d4178732eeb61bfd570f27925185372388a2396
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278574"
---
# <a name="task-1-create-the-ports"></a>工作 1： 建立連接埠
建立下列連接埠：左邊的 BeginDoc 和 EndDocOut，以及右邊包含 3 個作業的 JDEPort。  
  
|名稱和設定|作業|訊息類型 > 結構描述|  
|-----------------------|---------------|----------------------------|  
|BeginDoc<br /><br /> BeginDocType / 單向 / 內部<br /><br /> 我將總是在此連接埠接收訊息<br /><br /> 稍後指定|作業 1 要求-|BeginDocTest.B4200310Service_1。<br />F4211FSBeginDoc|  
|EndDocOut<br /><br /> EndDocType / 單向 / 內部<br /><br /> 我將總是在此連接埠傳送訊息<br /><br /> 稍後指定|作業 1 要求-|BeginDocTest.B4200310Service_1。<br />F4211FSEndDocResponse|  
|JDEPort<br /><br /> JDEPortType / 要求-回應 / 內部<br /><br /> 我將總是傳送要求並接收回應<br /><br /> 稍後指定**附註：** 如需其他作業，以滑鼠右鍵按一下 連接埠，然後選取新的作業。|作業 1 要求-<br /><br /> 作業 1 回應-<br /><br /> 作業 2 的要求-<br /><br /> 作業 2 回應 -<br /><br /> 作業 3 要求 -<br /><br /> 作業 3 回應-|BeginDocTest.B4200310Service_1。<br />F4211FSBeginDoc<br /><br /> BeginDocTest.B4200310Service_1。<br />F4211FSBeginDocResponse<br /><br /> BeginDocTest.B4200310Service_1。<br />F4211FSEditLine<br /><br /> BeginDocTest.B4200310Service_1。<br />F4211FSEditLineResponse<br /><br /> BeginDocTest.B4200310Service_1。<br />F4211FSEndDoc<br /><br /> BeginDocTest.B4200310Service_1。<br />F4211FSEndDocResponse|  
  
## <a name="see-also"></a>另請參閱  
 [工作 2： 建立訊息](../core/task-2-create-the-messages2.md)   
 [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes2.md)   
 [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape1.md)   
 [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape2.md)