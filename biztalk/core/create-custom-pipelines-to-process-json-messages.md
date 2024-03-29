---
title: 建立自訂管線來處理 JSON 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b04faad1-b14b-4146-82c7-88a38d2a46a5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e28f825b1f26f3c080a02fd9a2e2bf8960a816fd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005991"
---
# <a name="create-custom-pipelines-to-process-json-messages"></a>建立自訂管線來處理 JSON 訊息
> [!NOTE]
>  本教學課程僅適用於 BizTalk Server。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供可用來處理 JSON 訊息內的管線元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。 在此步驟中，我們可以使用這些管線元件建立自訂的管線，可以在設定時使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。  
  
## <a name="create-a-custom-receive-pipeline"></a>建立自訂接收管線  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中的，從 [方案總管] 中，以滑鼠右鍵按一下專案，並指向**新增** > **新項目** > **接收管線**. 提供的管線名稱`JSONToXmlReceivePipeline.btp`，然後按一下**新增**。  
  
2. 內**解碼**階段新增**JSON 解碼器**。 中的其他階段和其他螢幕擷取畫面所示的管線元件，並儲存變更。  
  
    ![自訂接收管線](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")  
  
## <a name="create-a-custom-send-pipeline"></a>建立自訂傳送管線  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中的，從 [方案總管] 中，以滑鼠右鍵按一下專案，並指向**新增** > **新項目** > **傳送管線**. 提供的管線名稱`XmlToJSONSendPipeline.btp`，然後按一下**新增**。  
  
2. 內**編碼**階段新增**JSON 編碼器**。 中的其他階段和其他螢幕擷取畫面所示的管線元件，並儲存變更。  
  
    ![自訂傳送管線](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 處理 JSON 訊息](../core/processing-json-messages-using-biztalk-server.md)