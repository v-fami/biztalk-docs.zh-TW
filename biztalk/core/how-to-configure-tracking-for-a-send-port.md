---
title: 啟用 [追蹤傳送埠] |Microsoft 文件
description: 開啟訊息內文追蹤，並在 BizTalk Server 中的傳送埠上追蹤訊息屬性
ms.custom: ''
ms.date: 12/13/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 223c417769086cc71f501b044410bf2d3e4cbc74
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2017
ms.locfileid: "26686629"
---
# <a name="configure-send-port-tracking-in-biztalk-server"></a>在 BizTalk Server 中設定傳送埠的追蹤
使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定追蹤傳送埠，例如選項，以檢視訊息內文和升級屬性。 這可以協助您監控 BizTalk 實作的狀況並找出任何瓶頸。 您設定的追蹤設定適用於傳送埠的所有執行個體。  
  
 如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>Prerequisites  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="enable-tracking-on-a-send-port"></a>啟用 [追蹤] 傳送埠  
  
1.  在**BizTalk Server 管理**、 依序展開 [BizTalk 群組] 和您傳送埠的 BizTalk 應用程式。  
  
2.  選取**傳送埠**、 以滑鼠右鍵按一下傳送埠、 選取**屬性**，然後選取**追蹤**。  
  
    > [!NOTE]
    >  一個傳送埠只能與一個傳送管線相關聯。 訊息內文追蹤已停用在傳送管線，不會追蹤在傳送埠。 在這類情況下，您可以停用該傳送埠上的「追蹤」選項。  
  
3.  使用下列詳細資料，若要啟用的追蹤選項，然後再選取**確定**以儲存變更。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**追蹤訊息內文-連接埠處理前要求訊息**|儲存和追蹤訊息內容，才能接收訊息。 <br/><br/> **請注意**： 請務必啟用訊息內文管線追蹤，才能成功追蹤連接埠處理前的回應訊息。|  
    |**追蹤訊息內文-連接埠處理後要求訊息**|儲存並收到訊息之後，追蹤訊息內容。|  
    |**追蹤訊息內文-連接埠處理前回應訊息**|儲存並傳送訊息之前，追蹤訊息內容。 只適用於請求-回應傳送埠。|    
    |**追蹤訊息內文-連接埠處理後回應訊息**|儲存並傳送訊息之後，追蹤訊息內容。 只適用於請求-回應傳送埠。|  
    |**追蹤訊息內文-連接埠處理後回應訊息**|追蹤輸入訊息的升級屬性。|  
    |**追蹤訊息屬性-連接埠處理後要求訊息**|追蹤輸出訊息的升級屬性。|  
    |**追蹤訊息屬性-連接埠處理前回應訊息**|儲存並傳送訊息之前，會追蹤訊息屬性。 只適用於請求-回應傳送埠。|   
    |**追蹤訊息屬性-連接埠處理後回應訊息**|儲存並傳送訊息之後，會追蹤屬性。 只適用於請求-回應傳送埠。|   
  
## <a name="see-also"></a>請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)
