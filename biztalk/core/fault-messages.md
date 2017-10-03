---
title: "錯誤訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages
- ports, error messages
- Catch Exception block [Orchestration Designer], error messages
- error messages, receiving
- messages, errors
- error messages, sending
ms.assetid: 33d62260-b5e0-4d14-b2d2-996733d588e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4127fd5718ee910cb298436c0d0f7058ccba55b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fault-messages"></a>錯誤訊息
要求回應連接埠可能具有與其關聯的錯誤訊息，因此如果在傳送要求後出現錯誤，回應的服務即可對要求者通訊錯誤，以便代替回應。  
  
 要求回應連接埠的每項作業都可以處理任意數目的不同錯誤。 錯誤訊息可以具有任何訊息類型，不過訊息類型對作業必須是唯一的，而且不能是在該連接埠作業中回應所使用的類型。  
  
## <a name="receiving-fault-messages"></a>接收錯誤訊息  
 如果您的連接埠先傳送要求，然後再接收回應，您就可以使用該作業來接收一個或多個不同的錯誤訊息類型。  
  
 您可以設定**Catch 例外狀況**區塊來處理傳入的錯誤訊息從做為其例外狀況物件類型的要求-回應連接埠作業選取適當的錯誤。  
  
## <a name="sending-fault-messages"></a>傳送錯誤訊息  
 如果您的連接埠先接收回應，然後再傳送要求，您就可以使用該作業來傳送一個或多個不同的錯誤訊息類型。  
  
 例如如果您的協調流程碰到錯誤狀況而擲回例外狀況，您可以傳送錯誤訊息從**Catch 例外狀況**區塊處理例外狀況。 您可以建構具有適當類型的錯誤訊息，以便將情況傳達給參與的服務，並在將於連接埠作業中使用對應錯誤的「傳送」圖形上指定錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況](../core/exceptions.md)