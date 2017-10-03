---
title: "如何新增錯誤 Message1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- fault messages, adding
- adding, fault messages
- faults, adding messages
ms.assetid: 9d21de6b-c1a5-46e9-a9dc-d6aa7b5fe34b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87ef85460f6ca6aea046ef9efff60fd198664cd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-fault-message"></a>如何新增錯誤訊息
您一開始建立連接後端系統的連接埠時，會包含要求和回應。 您必須新增錯誤以擷取例外狀況。  
  
### <a name="to-add-a-fault-message"></a>若要新增錯誤訊息  
  
1.  以滑鼠右鍵按一下**連接埠作業**，然後選取**新錯誤訊息**。  
  
     A**錯誤**之下**要求和回應**在連接埠。  
  
2.  在**協調流程檢視**畫面上，以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。  
  
     Message_3 隨即建立，您可將它專門指派給該錯誤。  
  
3.  以滑鼠右鍵按一下**Message_3**存取**屬性**視窗。  
  
    1.  設定**訊息類型**。  
  
    2.  選取**結構描述**，然後選取從**參考組件**。  
  
         這會開啟**選取成品類型**視窗。  
  
    3.  向下捲動並選取完整格式的錯誤。  
  
         名稱是**BTS。SOAP_Envelope_1__1.fault**。 按一下**確定**接受選擇並關閉視窗。  
  
4.  以滑鼠右鍵按一下**錯誤**存取**屬性**視窗。  
  
    1.  設定**訊息類型**。  
  
    2.  選取**結構描述**，然後選取從**ref**組件。  
  
         這會開啟**選取成品類型**視窗。  
  
    3.  向下捲動並選取完整格式的錯誤。  
  
         名稱是**BTS。SOAP_Envelope_1__1.fault**。  
  
    4.  按一下**確定**接受選擇並關閉視窗。  
  
         ![](../core/media/siebeladapter-17-exceptionhandling-addscope.gif "SiebelAdapter_17_ExceptionHandling_AddScope")  
  
5.  為錯誤命名後，您會將此名稱設定為 CatchException 的例外狀況物件型別。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling2.md)